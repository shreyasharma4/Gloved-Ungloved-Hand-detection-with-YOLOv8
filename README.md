\# Gloved vs Bare Hands Detection



\## Dataset  

\- Name: gloves and bare hands detection dataset  

\- URL: \[https://universe.roboflow.com/dolphin-nog9y/gloves-and-bare-hands-detection/dataset/2/download/yolov8](https://universe.roboflow.com/dolphin-nog9y/gloves-and-bare-hands-detection/dataset/2/download/yolov8)  



\## Model Used  

\- YOLOv8n (nano version) pretrained on COCO  



\## Preprocessing \& Training  

\- Images resized to 640x640 before training  

\- Standard augmentations like mosaic and horizontal flipping used  

\- Batch size of 16, training done on CPU so it took time  

\- Training limited to 3 epochs due to hardware constraints  



\## What Worked  

\- Pretrained YOLOv8 weights helped the model learn faster  

\- Augmentations improved robustness to different backgrounds and lighting  

\- Adjusting confidence threshold balanced false positives and missed detections  



\## What Didn’t Work / Challenges  

\- Training on CPU was slow, so fewer epochs could be run  

\- Model struggled with partly hidden hands or hands in shadows  

\- Small hands were sometimes missed or detected with low confidence  



\## Class Labels Note  

The dataset includes three classes: 'gloverotation' ,'paper' and 'surgical-gloves'

For this task, gloverotation and surgical-gloves are treated as gloved hands, while paper corresponds to bare or ungloved hands.  

This means the detection output covers the assessment’s requirement of distinguishing gloved vs bare hands by grouping these classes accordingly.  

I’ve used the dataset as provided to keep the labeling consistent and clear.



\## How to Run

1\. Place your dataset YAML and image folders as per the config.  

2\. Put your test `.jpg` images into a folder named `test\_images`.  

3\. Run the Jupyter notebook cells one by one (Shift + Enter).  

4\. Annotated images will be saved in the `output` folder.  

5\. Detection logs in JSON format will go into the `logs` folder.

You can also run the command-line script with:
python detection\_script.py --weights runs/detect/train14/weights/best.pt --input test\_images --output output --logs logs --confidence 0.3    # you can change the confidence threshold here


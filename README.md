# WBC_Detection Final 

This README provides an overview of the code and steps involved in multi-class object detection using Faster-RCNN for detecting white blood cells (WBC) in images. The code is designed to run on Google Colaboratory, a cloud-based Jupyter notebook environment.

## Installation

Before running the code, you need to install the required dependencies. The following packages are required:

- `pycocotools`: Required for evaluation of the object detection model.
- `torchvision`: Required for loading the pre-trained Faster R-CNN model.

Run the following command to install the necessary packages:

```python
!pip install pycocotools --quiet
```

## Dataset

The dataset consists of images of white blood cells, along with their corresponding annotations. The annotations are in XML format and contain bounding box coordinates for each white blood cell along with its class label. The class labels are encoded with numerical values, and a mapping of class labels to their encoded values is provided.

To prepare the dataset for training, the provided XML annotations are converted to YOLOv5 format. The images and converted annotations are organized into a custom dataset class (`MyDataset`) that can be used with PyTorch's DataLoader.

## Training

The object detection model is based on Faster R-CNN, a state-of-the-art architecture for object detection. The pre-trained Faster R-CNN model is loaded, and the final fully connected layer is replaced with a new one to accommodate the number of classes in the dataset.

The model is trained using the provided dataset and optimized using the Adam optimizer. The learning rate is adjusted using a learning rate scheduler. The model is trained for a specified number of epochs.

## Testing

After training, the model is loaded, and the testing phase begins. Images are passed through the trained model to obtain predictions. The predicted bounding boxes, class labels, and confidence scores are obtained from the model's output. A threshold is applied to filter out low-confidence predictions. The final predictions are displayed along with the original images, showing the detected white blood cells and their corresponding class labels and confidence scores.

![wbc](https://github.com/ozzmanmuhammad/White-Blood-Cells-Detection/assets/93766242/c0b44a07-0161-4f9f-8504-d0cdc5b3818f)

## Note

- The code assumes that the dataset is stored in the specified directory structure, with images in the `images` folder and annotations in the `annotations` folder.
- The number of classes in the dataset should be specified as `num_classes` in the code.
- The model is trained using a GPU if available; otherwise, it falls back to CPU.

Please note that this is just a brief overview of the code. For more detailed information, refer to the actual code in the provided Jupyter notebook (`WBC_Detection_final.ipynb`).

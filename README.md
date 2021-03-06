# Chinese Character Classification through CNNs

Convolutional neural networks (CNNs) have been used extensively in the problem of handwritten character classification. Since handwriting differs from person to person, computers can often struggle to match an image with the corresponding character. Interested in learning about CNNs myself, I decided to give this problem a try by training and testing on Chinese characters from the CASIA dataset (http://www.nlpr.ia.ac.cn/databases/handwriting/Home.html).

## Data Preprocessing

The images were extracted from the CASIA dataset using an open-source library called PyCasia. They were then rescaled to 128 by 128, converted to grayscale, and randomly cropped to 96 by 96 for training. The images in the validation data set were simply rescaled to 96 by 96.

In the end, the training dataset was composed of 897760 images with 3755 classes, while the testing dataset was composed of 224000 images.

## File Roles

To run the CNN, type in the following commands (in order):
```
python3 dict.py   # creates a dictionary of the characters in the training dataset

python3 image.py  # reads the images through PyCasia and creates the training and testing tensors

python3 main.py   # builds the model
```

The best model is saved to a file called model.pt, which can be reloaded using Pytorch for future use.

## Model Framework

Here, I implement a two-layer CNN with two max-pooling layers and one fully connected layer. In the future, I may change a few of the parameters, but so far, this setup has achieved the highest validation accuracy.

## Results

Overall, the classifier achieved a best accuracy of **77.90%** on the validation dataset. Interestingly, while the accuracy on the training dataset continued to increase for all 100 epochs, the accuracy on the validation dataset remained somewhat stable after Epoch 60 (hovering around 77%).

![results](https://raw.githubusercontent.com/williamhu99/chinese-character-classifier/master/Images/results.png)

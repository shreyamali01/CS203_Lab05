# CS 203: Software Tools & Techniques for AI
**IIT Gandhinagar**  
**Sem-II - 2024-25**

# Lab 05: Data Augmentation & Model Training for Image Classification

## Task 1 : Data Augmentation

a. Data Downloaded from : https://www.kaggle.com/datasets/samuelcortinhas/cats-and-dogs-image-classification?select=test
b. The Dataset Contains total 70 Images for Cats and Dogs Respectively. 
c. On splitting the train-test dataset in 80:20 % ratio, we get 56 images in train set for each cat and dog. And 14 images in test set for each cat and dog. 

![Plot of Train and Test Set : Cats and Dogs](plot1.png)

d. A custom data augmentation function was implemented using the **Augly** library, applying the following **10 augmentation techniques**:

- Rotation
- Crop
- Blur
- Brightness
- Contrast
- Saturation
- Horizontal Flipping
- Vertical Flipping
- Scaling
- Padding
- Random Noise

Each Image in the given dataset was augmented 3 times (with combination of above mentioned techniques) twice. As a result, we initially had 112 (56 cats + 56 dogs) images, after applying augmentation we have, 112x2 = 224 augmented images. 

![Plot of Train and Test Set : Cats and Dogs](plot2.png)

### Dataset Statistics:

| Dataset Type           | Original Count | Augmented Count | Total Count  |
|------------------------|----------------|------------------|--------------|
| **Training Set**        | 112 images     | 224 images     | 336 images |
| **Testing Set**         | 28 images     | 0 images         | 28 images   |


## 3. Model Training

The **ResNet-50** model from Hugging Face was used for both training tasks. The model was initialized with random weights.

- Model Architecture Details : ResNet-50 (Initial weights of both the models are same)
- Optimizer : Adam with a learning rate of 0.01
- Loss Function : Cross-Entropy Loss function 
- Number of Epochs : 7
- Batch Size : 32

![ResNet-50 Architecture](ResNet50.jpeg)

## 4. Evaluation Metrics

The following metrics were used to evaluate both models on the test set:

### Model 1 (Without Augmentation):
- **Accuracy**: 0.5714
- **Precision**: 0.5556
- **Recall**: 0.7143
- **F1 Score**: 0.6250

### Model 2 (With Augmentation):
- **Accuracy**: 0.7143
- **Precision**: 0.6667
- **Recall**: 0.8571
- **F1 Score**: 0.7500

## 5. Results Analysis

- The model trained on original dataset shows consistent loss reduction but with a low accuracy of 57.14%. This could possibly be due to overfitting.

- The model trained on augmented data shows higher final training loss but it has better accuracy as compared to the model trained on the original dataset. This shows that augmentation of data is preventing overfitting.

- For other parameters, the model trained on augmented data has higher precision, recall and F1 score. This indicates that the model trained on augmented data generalizes better giving us more accuracy. 

- For training losses over epochs in both the model, we observe that there are some fluctuations. These fluctuations can be avoided implementing optimal learning rate and number of epochs. 
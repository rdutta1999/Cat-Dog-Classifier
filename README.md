# Cat Dog Classifier
 Classifying images of Cats and Dogs
 
 Download the dataset from [Dogs vs Cats Redux: Kernels Edition](https://www.kaggle.com/c/5441/download-all) on Kaggle.
 
 We then extract the data and place the images in the following manner:- 
 
 <pre>
 ├─── Cats vs Dogs - Classifier.ipynb
 ├─── test
      ├─── 1.jpg
      ├─── 2.jpg
      ├─── 3.jpg
      ├─── ..
      ├─── ..
      ├─── 12488.jpg
      ├─── 12499.jpg
      └─── 12500.jpg
 └─── train
      ├─── cat.0.jpg
      ├─── cat.1.jpg
      ├─── ..
      ├─── ..
      ├─── cat.12498.jpg
      ├─── cat.12499.jpg
      ├─── dog.0.jpg
      ├─── dog.1.jpg
      ├─── ..
      ├─── ..
      ├─── dog.12498.jpg
      └─── dog.12499.jpg 
     
</pre>

We have used **Keras ImageDataGenerator** for performing **Data Augmentation**.

We use **InceptionV3** as the base model with the **'imagenet' weights**. We remove the **Fully connected Layers** at the top, and then add a **Global Average Pooling Layer** and a **Dense Laye**r with **sigmoid activation** function. We **freeze** the entire Convolutional part of the Network and only train the last Dense layer for **20 epochs**. After that, we save the model and move on to **finetuning** the model.

Now, we **unfreeze** the Convolutional part of the model and re-train the entire model for **30 epochs**. We use **Adam** as the optimizer with a very **small learning rate(1e-5)**, and use Checkpoints to save the model when it has the highest Validation accuracy.

We see that after the last epoch, the model has the best combination of Training and Validation accuracy, so we save it as the final model and use it to predict the Test cases, which got us a score(LogLoss) of **0.14932** when submitted to Kaggle. 

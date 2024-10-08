
# Image Segmentation (Water body segmentation in Satellite Images)

A collection of water bodies images captured by the Sentinel-2 Satellite. Each image comes with a black and white mask where white represents water and black represents something else but water. The masks were generated by calculating the NWDI (Normalized Water Difference Index) which is frequently used to detect and measure vegetation in satellite images, but a greater threshold was used to detect water bodies. The project aims to segment the water bodies.


## Dataset source
https://www.kaggle.com/datasets/franciscoescobar/satellite-images-of-water-bodies/download?datasetVersionNumber=2
##  U-Net for Image Segmentation

This repository contains an implementation of the U-Net architecture, a convolutional neural network designed for image segmentation tasks. U-Net is particularly effective for applications where precise localization is essential, such as biomedical image segmentation, satellite image analysis, and more. The architecture consists of a symmetric encoder-decoder structure, where the encoder captures context and the decoder enables precise localization through upsampling. Skip connections transfer high-resolution features from the encoder to the decoder, improving segmentation accuracy.

Dropout layers have been incorporated into the model to prevent overfitting by randomly disabling a fraction of neurons during training, ensuring better generalization on unseen data. This implementation is optimized for flexibility and can be easily adapted to various segmentation tasks.
## Callbacks

The U-Net model is trained using a set of helpful callbacks to optimize performance and monitor progress:

ModelCheckpoint: Saves the model after every epoch, but only if there is an improvement in the validation loss (val_loss). The save_best_only=True argument ensures that only the model with the best performance is saved. In this case, the model is saved as model_for_watershed.keras.

EarlyStopping: Monitors the validation loss and stops the training process if there is no improvement for a set number of epochs (in this case, 3 epochs). This helps prevent overfitting and unnecessary computation by halting training once the model has reached its optimal performance.

TensorBoard: Logs the training and validation metrics (such as loss and accuracy) to a directory (logs) which can be visualized in TensorBoard. This allows tracking of training progress, helping in identifying overfitting or underfitting trends over time.

ShowProgress: A custom callback that visually compares the predicted segmentation mask with the original ground truth mask after each epoch. This allows the user to observe how the model’s predictions improve during training.

# CycleGAN for Image-to-Image Translation

This repository contains the complete implementation of a CycleGAN model for unpaired image-to-image translation between **human faces** and **animal faces** (cats and dogs). 

---

## Project Summary

- **Title**: CycleGAN – Face to Animal Image Translation  
- **Environment**: Google Colab + PyTorch  
- **Dataset**: Human and Animal face images (unpaired)

---

## Objective

Train and evaluate a **CycleGAN** model to learn a bidirectional translation between:
- `Domain A`: Human Faces
- `Domain B`: Animal Faces (Cats & Dogs)

---

## Dataset Structure

All datasets are stored in Google Drive and extracted into:

```
CycleGAN_Dataset/
 ┣ trainA/  ← Human faces
 ┣ testA/
 ┣ trainB/  ← Animal faces (cats + dogs)
 ┣ testB/
```

Datasets include:
- `face_img.zip` containing `face_align_celeba.zip` and `UTK Face Cropped.zip`
- `cat_and_dog-1.zip` containing `cat_face.zip` and `dog faces.zip`

---

## Implementation Highlights

- **Automated ZIP Extraction**: From Google Drive using nested archive unpacking with validation
- **Dataset Cleaning & Splitting**: Shuffled and split into 80/20 for training and testing
- **Organized Directory Setup**: Reorganized into `trainA/B` and `testA/B` with consistent naming
- **CycleGAN Training**: Resumed training across multiple epochs using checkpoints
- **Google Drive Integration**: Model checkpoints and dataset folders persisted in Drive
- **Visual Outputs**: Used `results` folder to show real-world translations

---

## Training Commands

Training executed via:
```bash
!python train.py   --dataroot "/content/drive/MyDrive/CycleGAN_Dataset"   --name "human2animal"   --model "cycle_gan"   --direction "AtoB"   --batch_size 4   --n_epochs 20   --n_epochs_decay 15   --lr 0.0001   --lambda_A 10 --lambda_B 10   --save_epoch_freq 5   --gpu_ids 0   --checkpoints_dir "/content/drive/MyDrive/CycleGAN_checkpoints"
```

Model training was resumed at epoch 5 with modified learning rate and λ values.

---

## Libraries Used

- PyTorch  
- Python (3.x)  
- Google Colab  
- Matplotlib  
- OpenCV  
- ZIP & OS Modules  

---

## Sample Results

Translated test images from human → animal and vice versa are stored in:
```
pytorch-CycleGAN-and-pix2pix/results/human2animal/test_latest/images/
```

Example file names:
- `human_AtoB.png` (Generated animal face)
- `human_BtoA.png` (Reconstructed human face)
- `human_real_A.png` (Original input image)

---

## Author

- **Pranav Sunil Raja**  
- MSc Data Science & AI, Newcastle University  
- GitHub: [@pranavsraja](https://github.com/pranavsraja)

---

## License

This project is for educational use only. All datasets used follow original licensing and are hosted privately in Google Drive.

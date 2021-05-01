# GoalGAN_folked

This repository provides the redo instruction of Goal-GAN system, presented at [ACCV 2020](http://accv2020.kyoto/)(Oral)

[<b>Goal-GAN: Multimodal Trajectory Prediction Based on Goal Position Estimation</b>  
Patrick Dendorfer, Aljoša Ošep, Laura Leal-Taixé](https://arxiv.org/abs/2010.01114)  

## Motivation
In this paper, an interpretable and end-to-end trainable model for human trajectory prediction. 
The task of trajectory prediction as an intuitive two-stage process: (i) goal estimation, which predicts the most likely target positions of the agent, followed by a (ii) routing module, which estimates a set of plausible trajectories that route towards the estimated goal. 
We leverage information about the past trajectory and visual context of the scene to estimate a multimodal probability distribution over the possible goal positions, which is used to sample a potential goal during the inference. 


## Model
GOALGAN consists of three key components: Motion Encoder (ME), Goal Module (GM), and Routing Module (RM).


The model is trained with an adversarial loss for which the discriminator classifies the predictions as 'real/fake' by considering input trajectory, prediction, and visual input of the scene.
## Visualizing Multimodality      

## Reference

```
@inproceedings{dendorfer2020accv,
  title={Goal-GAN: Multimodal Trajectory Prediction Based on Goal Position Estimation}, 
  author={Patrick Dendorfer and Aljoša Ošep and Laura Leal-Taixé},
  year={2020},
  booktitle={Asian Conference on Computer Vision},
  }
```


## Setup

All code was developed and tested with Python 3.6.9, PyTorch 1.7.1., and PyTorch-Lightning 0.9.0.

You can setup a virtual environment and install the required packages by following the instruction in environment_build.txt

## Training Models
To train your models set up the config ```yaml``` files in the config folder, adjusting the [Hyperparameters](HYPERPARAMETERS.md).
To start the training run:
```
python run.py
```
You can also change the configuration by directly typing into the command line, e.g.:
```
python run.py batch_size=64 lr_scheduler_G=1e-4
```
The training process and models are saved and logged with tensorboard. The final model performance is evaluated on the test set and save in 'results.pt'. You can use this [script](/utils/collect_results.py) writing all results into a csv in [resultCSV](resultCSV).


## Synthetic Dataset


## Data Format
To run or re-train the model with new data provide the trajectories in a txt file with the following format:

```<frame_id>, <ped_id>, <x>, <y>```

As well as RGB images of the corresponding scene in the dataset folder.


## Contact
If you find any bugs or have any questions, please open an issue or contact the other via mail (patrick.dendorfer@tum.de).

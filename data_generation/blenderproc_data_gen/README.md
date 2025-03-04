# Synthetic Data Generation with Blenderproc

## Installation
Blenderproc can be installed with pip:
```
pip install blenderproc
```
If you run into troubles, please consult the [project's own github page](https://github.com/DLR-RM/BlenderProc).


## Usage

[Blenderproc](https://github.com/DLR-RM/BlenderProc) is intended to create a single scene and render multiple frames of it. Adding and removing objects (such as varying the number of distractors) will cause memory bloat and poor performance.  To avoid this issue, we use a batching script (`run_blenderproc_datagen.py`) to run a standalone blenderproc script several times.



## Usage example:

Run the blenderproc script 5 times, each time generating 1000 frames. Each frame will have five copies of the object and ten randomly chosen distractor objects:
```
./run_blenderproc_datagen.py --nb_runs 1 --nb_frames 10 --path_single_obj ../models/Ketchup/google_16k/textured.obj --nb_objects 5 --distractors_folder ~/data/google_scanned_models/ --nb_distractors 10 --backgrounds_folder ../dome_hdri_haven/
```

All parameters can be shown by running
```
python ./run_blenderproc_datagen.py --help
```
Note that, as a blenderproc script, `generate_training_data.py` cannot be invoked with Python. It must be run via the `blenderproc` launch script.

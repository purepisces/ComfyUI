If your machine doesn't have an NVIDIA GPU, you won't be able to use CUDA. 

Thus I use a aws and ec2 instance that using NVIDIA GPU and I use g5.xlarge

1. SSH then Git Clone to AWS


```python
git clone https://github.com/comfyanonymous/ComfyUI.git
```

2. Install necessary package and Install ComfyUI-Manager: which is extremely useful for install missing custom_nodes in workflow

```python
pip install -r requirements.txt
cd ComfyUI/custom_nodes
git clone https://github.com/ltdrdata/ComfyUI-Manager.git
#run the code
python3 main.py
```

3. Download a workflow json:  https://openart.ai/workflows/templates and press load button to upload it: e.g. I download https://openart.ai/workflows/openart/-/lkOtNJ2UexVd6vK0kYhd

4.  When click queue prompt, it will get an error, then put a corresponding checkpoint in the ComfyUI/models/checkpoints folder,  you can download from the website: https://huggingface.co/autismanon/modeldump/blob/main/dreamshaper_8.safetensors
    
    ```python
    #
    Prompt outputs failed validation
    CheckpointLoaderSimple:
    
    - Value not in list: ckpt_name: 'dreamshaper_8.safetensors' not in []
    ```
    
5. Click queue prompt again, then you can see the process from your local port and the logging info from terminal:
    
    ```python
    ubuntu@ip-xx-xx-xx-xxx:~/ComfyUI$ python3 main.py
    ...
    got prompt
    model_type EPS
    Using xformers attention in VAE
    Using xformers attention in VAE
    clip missing: ['clip_l.logit_scale', 'clip_l.transformer.text_projection.weight']
    loaded straight to GPU
    Requested to load BaseModel
    Loading 1 new model
    Requested to load SD1ClipModel
    Loading 1 new model
    100%|██████████████████████████████████████████████████████████| 25/25 [00:02<00:00, 11.23it/s]
    Requested to load AutoencoderKL
    Loading 1 new model
    Prompt executed in 4.36 seconds
    ```

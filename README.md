# logbook

Particle Picking:
  * Use Yolov8 for particle picking
    - Preformed well on synthetic dataset
  
  * Cross train using cryoPPP
      - Script to convert data form cryoppp Entries to YOLO format
          * Done; multiprocessed for speed
      - Preformed markedly worse when cross trained on cryoppp
      
  * Script to convert data form cryoppp Entries to YOLO format
    - Done; multiprocessed for speed
    
  * Validate Yolov8 using reconstruction of picked particles
	  - Low precision/recall on test set
  
  * Lamma vision
    - cryo em lacks detailed image annotations (only euler angles/xy shifts) 
      
  * TODO:
    Reimplement original Yolo algorithm (Redo CrYOLO form scracth)
  

Particle Alignment:

  * Improve contrast by downscaling/low pass filtering (8 angstrom)
	  -  Downscaling to 8 Angstom did not improve mean angular error


  * Train CNN/ViT on synthetic cryoem Images
    - Loss to ~ 5 degrees

  * Faiss T-snee find unifying pattern in data
    - no pattern found by vectorizing images (length 16384 vectors are far too large)
    - Could be used to test pretrained feature extractors?
   
  * Develop a pipeline by outputting a .star file containing predicted angles for 3D reconstruction.
    - Works reasonable quickly by Batch paralelization 

  * Cross-Train Resnet and ViT then fine tune to in situ data
    - Resnet is trained performs worse than individual
    - ViT is limited by shift variance
    
  * Comparison of "ground truth error"
    - Implemented weighted loss function

  * Integrate Cryotransformer/yolov8 backbone in poET to regress rotation
    - Different set of features used for picking (low freq info) and alignment (hi freq info)
  
  * TODO:
    Dataset:
              Supplement Cesped by aligning Cryoppp particles
                - need to write cryosparctools script
    		relion autorefine in pseudoknot and in situ
    		make in situ training maps for cryosegnet fine tuning

    Model:
              apply cryosegnet to ribiosme/in situ
    		evauate using gisspa
    		try fine tuning
    		continue cross training
    Debug:
    		Train/test 10166_template
    		Reconstruct 10409 in cryoSparc
    		Try ab initio methods on our data (ribosome/in situ)
		continue 10166CS training
  		align using relion autorefine (taking confidence as (1 - norm(alignments3D/error)) is less reliable than rlnMaxValueProb)
			    

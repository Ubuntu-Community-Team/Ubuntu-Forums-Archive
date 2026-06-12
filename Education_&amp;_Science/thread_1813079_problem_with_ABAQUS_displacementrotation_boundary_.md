---
title: "problem with ABAQUS displacement/rotation boundary conditions"
date: 2011-07-27
forum: Education &amp; Science
---

### Post by kren_cudn on 2011-07-27
Hello! 

I am trying to simulate movement of some rigid body through some rigid ring in ABAQUS. I specify finite displacement/rotation boundary conditions for every DOF: each DOF in its own table with time increments, because I use explicit solver. Time increments are the same for every DOF. I would like to know; how exactly ABAQUS combines two or three rotation DOF in the same time (two angles). I have read this in ABAQUS documentation, and used the same mathematic, that I got in that documentation, to inversely calculate needed rotation inputs for boundary DOF, so I would get the right movement in simulation, but the movement is not right. Translations are ok, but rotations are not. ABAQUS uses Euler convention for finite rotations. Is that true? Could there be problem because of NIgeom is on? Error starts in simulation, when two rotations are used in the same time, for only one rotation it works ok. I would really appreciate, when someone would explain me mathematically, how are two or three rotation DOF from boundary condition applied in the same time in simulation. Thank you very much in advance. 

Best wishes, 

Gasper

---


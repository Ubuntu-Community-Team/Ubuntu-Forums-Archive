---
title: "Interesting problem needs to find a good Physics Simulator"
date: 2008-10-31
forum: Education &amp; Science
---

### Post by Grandma_DOG on 2008-10-31
I need to throw a rock at the atmosphere at 20,000 mph and have an airflow simulator model its breakup and fall pattern.  Then do it over and over again 100,000 times to do a monte carlo analysis.

Any ideas where to start?  The google searches I've done and SAL searches don't look promising.

---

### Post by Nirva on 2008-10-31
You could write a simulation with matlab ?

---

### Post by Grandma_DOG on 2008-10-31
> **Nirva said:**
> You could write a simulation with matlab ?

No, I don't know matlab, don't have time to learn it, don't know if it could even do it.  I'm not a programmer.  But if someone knows a package that will work, I've got a budget to contract for a short term project.

---

### Post by WW on 2008-11-01
Do you already have a good understanding of the model of this process, or is figuring that out part of the problem to be solved?

For example, a "rock" could be modeled as a point mass, a sphere, an ellipsoid, a polyhedron, etc. (Since you mention air flow, a point mass is presumably far too simple.)  What do you already know about how to model the breakup of the rock?

---

### Post by Grandma_DOG on 2010-08-18
Bump.

---

### Post by lordhaworth on 2010-08-19
> 
Do you already have a good understanding of the model of this process, or is figuring that out part of the problem to be solved?

For example, a "rock" could be modeled as a point mass, a sphere, an ellipsoid, a polyhedron, etc. (Since you mention air flow, a point mass is presumably far too simple.) What do you already know about how to model the breakup of the rock? 


Yeah we really need a bit more info as advised above, there are a huge range of possibilites wrt the kind of thing you are asking. The nature of the rock is a pretty important thing (how will we know when it should break up etc). 


> 
No, I don't know matlab, don't have time to learn it, don't know if it could even do it. I'm not a programmer. But if someone knows a package that will work, I've got a budget to contract for a short term project. 

Even if you dont expect to do any programming, you will have to build your model into the code that you will be using - it is highly unlikely that you will be able to point and click some model options then set it running.

---

### Post by lordhaworth on 2010-08-19
Let me ask some questions/make suggestions:

     1) You will probably need to have a simulation which is "comoving" with the ball until breakup. Otherwise you will have a huge distance travelled (given the speed of the ball) and a very small ball ----> poor spatial resolution. In short have a stationary ball with flow moving around it at 20,000 mph until it breaks up.

     2) upon breakup, (or does the sim start at breakup? see below) you will need to allow the simulation grid to increase in spatial scale so that the components of the rock can be traced. 

     3) how interested are you in what happens to the rock before breakup? It would be relatively easy to model what happend to x amount of bits in a non-attractive cluster when exposed to 20,000 mph flow, but it is not so easy to model a ball being deformed etc until breakup. In short, I would start with a number of pieces close together but not "stuck together" at t=0 and then expose that to flow - this may not be accurate enough for you (you would also have to ensure that the rock was already surrounded by flow before turning the hydrodynamics on, because you dont want it to get hit by a shock front).

Now, I know I havnt answered your question about what resources there are code-wise, but you really need to know what you want to model first. There are a number of hydrodynamical codes out there, but which one you need will depend on how complex your model is.

---

### Post by MalcomWagon on 2010-08-19
Thanks for solve problems. Do you already have a good understanding of the model of this process, or is figuring that out part of the problem to be solved?

---

### Post by mikero1959 on 2010-08-19
I agree it's vital to know what you want from this model, and in what detail (eg does the "fall" mean you want to get a statistical distribution of how the rock particles diverge from the parent rock over time, or do you want to track the x, y, z, co-ordinates of each rock particle, or something else?), and then repeat this 100,000 times.
 
Depending on what accuracy you are trying to achieve, maybe you could look into speaking to a game coder. They model explosions every day of their life, including tracking the motion of each particle, as it spreads away from the explosion source. They use the Physyx library within NVidea CUDA enabled graphics cards - allowing the particles to be modelled in parallel, thereby speeding up the calculation times.
 
Just a thought.
 
Mike:D

---


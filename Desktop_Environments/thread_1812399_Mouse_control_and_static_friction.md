---
title: "Mouse control and static friction"
date: 2011-07-26
forum: Desktop Environments
---

### Post by pinery on 2011-07-26
Talking to myself, out loud, about Mouse Control. There's more to this that I don't know about.. so the solutions and analysis are just specific. Forgive me for restating known stuff. 

Problem: 
[INDENT]Gaming and quick mouse movements sometimes result in the mouse cursor moving with unexpected results. This is demonstrable and becomes visible in slow extended mouse movements, for example when drawing a line freehand or trying to select a thin window border. 
[/INDENT]Analysis: 
[INDENT]Static friction is usually greater than kinetic friction. This results in the body of the mouse experiencing higher order movements when moved on non ideal surfaces that are not frictionless or fluid. 
[/INDENT]Aside: looking at a linear movement, position of mouse is given in x displacement from an origin. Velocity is then k*x,  acceleration is k*x^2, jerk is k*x^3, and there are potentially higher order movement characteristics. 

Solutions:


[LIST=1]
[*]The optional addition of a smoothing or integrating term to the mouse control algorithm to reduce the transient movement effects of static friction. This is difficult for a user.
[*]Reduction of static friction by selecting mouse pads that have slippery surfaces. Teflon comes to mind. This is easier to implement.. usually.
[/LIST]

---


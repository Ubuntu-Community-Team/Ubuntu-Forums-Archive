---
title: "Visualizing Physics?"
date: 2013-01-10
forum: Education &amp; Science
---

### Post by Leopardson on 2013-01-10
Hi,

I'm screwing around with a simple Ising model in C, and have been working with SAW's for a while now. When I'm messing with my code, and I encounter a problem, I have no way of visualizing it without grabbing a piece of graphing paper or trying to brain it all out. 

I'm looking for some sort of graphical API for C I can use in my code to visualize the data I get in Physics-based programs on the fly. 
I don't know if OpenGL or any of the normal graphical API's are appropriate because I need simple graphical functionality, but with a lot of data. I need something that can take in tens of millions of points on a 2d graph and combine them into single pixels appropriately.

The problem I have with OpenGL is two-fold: First, the only tutorials on the internet I found were not only for different languages such as C# and c++, they were based on shaders. I have yet to find anything that will teach me to draw pixels in C and nothing more.  Second, I'm afraid that the fact that OpenGL is intended for gaming rendering will bring with it extra computing time that will bog down my programs and calculations with unnecessary and unwanted shader stuff.

Rather, I'm looking for something fast that will work well with C, and will work well for scientific uses rather than game-making stuff.

Is there a simple way to get OpenGL to do what I want? I.e, can I get OpenGL to draw a pixel where I tell it to draw a pixel and do absolutely nothing else special? Links to tutorials of some sort would be great. 
Are there any better graphical API's out there that are more intended for modeling?

Thanks!

---


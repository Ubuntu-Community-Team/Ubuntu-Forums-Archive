---
title: "Logout idea"
date: 2008-12-09
forum: General Help
---

### Post by T4nkFr4nk on 2008-12-09
This is just a crazy idea that is far passed my possibilities which are at best noob-like, at this point. 

Does anyone have the slightest idea if it is possible to make the desktop cube part of a robot that during login walks into the frame and gets up then walks out during log off. Any ideas? Anyone up for the challenge.

---

### Post by Baneblade on 2009-07-12
Seeing as nobody has replied to you in a long, long time.. id thought id give it a go.
Short answer: No.

Here is my understanding of why it most likely isnt possible.
While logging in and out the X Window manager is starting and stopping respectively. 
As this is required to draw things to the screen, nothing can be displayed until X is up. Once X is up and running it may be possible i guess? However, this would simply as additional runtime to your startup/shutdown/login/logout.
Also 3D animation, even pre-scripted stuff, would likely be processor/graphics intensive... I guess you could make it a video that plays.. but again, you'd have to wait for X.
There has recently been talk of Ubuntu adopting a similar system to Plymouth, allowing flicker free bootup, so your idea may be possible at some point in the future?
Here's hoping :)
Btw, did you mean the cube as the robots head? Cos that's what i'm picturing, and its rad ;)

---


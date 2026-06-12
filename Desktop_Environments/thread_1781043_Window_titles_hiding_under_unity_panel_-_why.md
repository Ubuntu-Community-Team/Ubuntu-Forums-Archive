---
title: "Window titles hiding under unity panel - why?"
date: 2011-06-12
forum: Desktop Environments
---

### Post by SirGe on 2011-06-12
While I think Unity has its many ups and downs, I found it usable enough to choose it as my default desktop, after some customization. 

Somewhere in tweaking the desktop with ccsm - or elsewhere - I did something boneheaded. Now when a new window opens at the top of the screen, its title bar is hidden under the Unity panel.

I could just wipe everything out and start over, but I kinda like the way things work on my desktop - with this exception. 

If anyone could suggest where I might look to figure out what is letting windows be placed all the way up under the panel, it would be great.

I did try creating a new account and looking at ccsm config export and comparing it to mine, but did not see anything useful. The only thing I changed with respect to window placement/handling, AFAIK, is disabling maximization at the top of the screen (in 'Grid' module); restoring that did not help.

Any hints?

**SOLVED**
The problem turns out to be caused by using a window type 'panel' in my conky config. Changing the window type to 'desktop' cured the problem. Did not dive any deeper to analyse exactly what conky 'panel' windows do to interfere with Compiz/Unity.

---

### Post by wildmanne39 on 2011-06-12
> **SirGe said:**
> While I think Unity has its many ups and downs, I found it usable enough to choose it as my default desktop, after some customization. 

Somewhere in tweaking the desktop with ccsm - or elsewhere - I did something boneheaded. Now when a new window opens at the top of the screen, its title bar is hidden under the Unity panel.

I could just wipe everything out and start over, but I kinda like the way things work on my desktop - with this exception. 

If anyone could suggest where I might look to figure out what is letting windows be placed all the way up under the panel, it would be great.

I did try creating a new account and looking at ccsm config export and comparing it to mine, but did not see anything useful. The only thing I changed with respect to window placement/handling, AFAIK, is disabling maximization at the top of the screen (in 'Grid' module); restoring that did not help.

Any hints?
Hi, look in my signature below this text you will see reset unity and compiz choose one to reset and that should fix you up. You can use this guide to get the cube or other effects to work in natty after you reset your system.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by SirGe on 2011-07-23
> **wildmanne39 said:**
> Hi, look in my signature below this text you will see reset unity and compiz choose one to reset and that should fix you up. You can use this guide to get the cube or other effects to work in natty after you reset your system.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
[-X Since the request specifically states that I want to identify the cause and that starting over is not desirable, I consider a response with reset hints to be less than constructive. Blatant and irrelevant trolling after an unhelpful response is not evoking my appreciation either.

---

### Post by fjgaude on 2011-07-23
Gosh, without fully knowing what was done to get you in the situation you find yourself, reseting ccsm is not much to ask.

Back track what you did to get to where you are, that might work.

---

### Post by wildmanne39 on 2011-07-23
Hi, given the information that you posted my recommendation was correct and I was only trying to help you, and it is a very simple procedure with no pain involved.

I am sorry that my recommendation offended you have a good day.

---


---
title: "Unable to use Extra Desktop Graphics"
date: 2008-03-09
forum: Desktop Effects &amp; Customization
---

### Post by TimTow on 2008-03-09
I cannot enable desktop extra effects.  
My Specs:

AMD board
nvidia GeForce 7300 
nvidia GeForce 8500 

     Both are linked with a ribbon connector

I am running dual monitors, one is an extension off the main desktop.

Can't seem to download xserver-glx, don't know why.  I also installed the compizconfig-advanced graphics manager, which did absolutely nothing...

before I docked the second video card on the board, it worked fine.

---

### Post by wozzinator on 2008-03-09
I'm assuming your using SLI if you've got 2 graphics cards in there, but I don't think you can use SLI with 2 different GPU's so that could be your problem. That or you need to install some more drivers to have SLI enabled in Ubuntu.

---

### Post by TimTow on 2008-03-09
I rectified the problem.  I think it was giving me so much trouble because one monitor is a dell e772c (like 10 years old) and the other is a new 24" widescreen, and apparently I can't control the output of resolution to two different monitors that are so grossly disproportioned in capabilities, so I consigned the dell to the closet and just upped the resolution on the new monitor so that I could run the compiz to the full effects.  Plus 24" monitor is ample desktop space for the time.  I am not sure if what I surmised is true or not, but I do have everything back to normal at least.  

On an unrelated subject:  I can't seem to install Gstreamer extra plugins (the ugly set), do you know which packages conflict with them because now I can't watch DVDs.  I had everything copasetic before catastrophe, but now when I retrace the old steps which cured the problems, I do not get the same outcome.  Thanks for responding, any new thoughts on this?

---


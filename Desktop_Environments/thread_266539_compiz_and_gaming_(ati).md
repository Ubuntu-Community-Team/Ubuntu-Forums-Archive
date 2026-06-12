---
title: "compiz and gaming (ati)"
date: 2006-09-27
forum: Desktop Environments
---

### Post by dyous87 on 2006-09-27
Hey everyone, I'm running Ubuntu Dapper Drake with compiz and xgI've tried installing games with Cedega (Star Wars Knights of the Old Republic, The Elder Scrolls, Oblivion, and Quake 2) none of which the install shield will even start. It comes up and then closes and nothing happens. Also I've tried installing some native games like Adonthell and even that will not work correctly. It comes up but is completely unplayable because it will not display correctly. I believe this has something to do with compiz because Cedega worked perfectly fine with Oblivion before I had installed Cedega. In the cedega system tests Open Gl Direct Rendering fails so maybe that has something to do with it?

Anyway my system specs are:
-Ubuntu Linux 6.06 (Dapper Drake)
-Kernel 2.6.15-27-386
-Intel Core duo T2300 1.66GHz
-2 GB RAM
-ATI Mobility Radeon X1400 w/ fglrx drivers 1.2 (2.0.5814 [8.25.18])

It would be great if anyone had a solution to this because I love the eye candy and over all "smoothness" that compiz supplies but I would also like to play some games here and there. I swear this is the last time I'm getting an ati graphics card lol ](*,) 

Thanks in advance
-Dave

---

### Post by vinnn on 2006-09-27
This isn't necessarily *just* because you're using an ATI graphics card but using an ATI card with XGL does kind of contribute to the problem.

When you setup XGL your are setting up a second X server that runns ontop the existing Xorg X server.
On ATI configurations Xorg runs on display :0 and XGL runs on display :1.

When you're launching your OpenGL applications they are defaulting to run on display :0, you want them to run on display :1

I got my games working OK over XGL by running them on display :93 (as stated [here]("http://forum.beryl-project.org/viewtopic.php?id=175")) although it is a workaround as beleive that Nvidia cards can run both X servers on display :0

What you have to do is change your XGL startup script so you start XGL with **-xorgAc** as an option. Then you start your game/3D app as ```
DISPLAY=:93 programname
```
If you're launching the game from an icon, edit the icon and stick **DISPLAY=:93 ** in front of the program name.


Stuff like this is bound to happen though until us ATI users have AIGLX support in the proprietory drivers, AIGLX runs as an extension within the existing Xorg X server so we won't be mucking about with 2 Xservers.
Ubuntu Edgy is touted to have AIGLX ready to go when it's released.

---

### Post by Ensnared on 2006-09-27
Running 3d games using Xgl and Compiz don't work, and I have the same experiences with installers crashing when run through Cedega.

I suggest you take a look at [this thread](http://ubuntuforums.org/showthread.php?t=176636) for various tips and workaround on how to make it work. Since you have an ATI board, I believe your only option is to run the game in its own X-session, but this may have changed since I replaced my ATI with an nVidia.

In general though, nVidia is superior by far when it comes to gaming in Linux, simply because ATI's Linux-drivers are horrible by comparison.

---

### Post by dyous87 on 2006-09-29
> **vinnn said:**
> 
When you're launching your OpenGL applications they are defaulting to run on display :0, you want them to run on display :1

I got my games working OK over XGL by running them on display :93 (as stated [here]("http://forum.beryl-project.org/viewtopic.php?id=175")) although it is a workaround as beleive that Nvidia cards can run both X servers on display :0

What you have to do is change your XGL startup script so you start XGL with **-xorgAc** as an option. Then you start your game/3D app as ```
DISPLAY=:93 programname
```
If you're launching the game from an icon, edit the icon and stick **DISPLAY=:93 ** in front of the program name.

How exactly would I change my xgl startup script with -xorgAc and where is that file located??

---

### Post by vinnn on 2006-10-02
That would depend on what how-to you used to set up Xgl. The instructions you followed would have taken you through creating a script or gdm option to start Xgl.

---

### Post by cptnapalm on 2006-10-02
There is a little script you can use called nonXgl which you put before the app name someplace after editing the xgl start up script.

---

### Post by dyous87 on 2006-10-02
Ok so after i find my start up script how do i set -xorgAc as an option?

And is there and possible way for me to find the location of that script, I'm not sure what tutorial I followed to set up compiz???:confused:

---

### Post by dyous87 on 2006-10-03
i found /usr/bin/compiz-start would that be my start up script?

---

### Post by ReiKn on 2006-10-23
> **dyous87 said:**
> Ok so after i find my start up script how do i set -xorgAc as an option?

And is there and possible way for me to find the location of that script, I'm not sure what tutorial I followed to set up compiz???:confused:

At least for me the script is /usr/bin/startxgl.sh

But when I added the option -xorgAc, gnome didn't start anymore, I just got an empty brown screen.

---


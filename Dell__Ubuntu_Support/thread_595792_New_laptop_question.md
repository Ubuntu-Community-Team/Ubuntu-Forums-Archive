---
title: "New laptop question"
date: 2007-10-29
forum: Dell  Ubuntu Support
---

### Post by fisting_mayfield on 2007-10-29
My girlfriend is thinking of purchasing a Dell XPS1330 notebook computer.  She needs to keep windows on there for warranty (when she rang dell she was told that if she formatted the hdd and installed Ubuntu as the sole OS that they would assume that as she has removed the "recommended" OS she  has voided the warranty for the system, *including* hardware) but she wants to install ubuntu on a second partition.
Before she spends the money I just want to check that the computer is Ubuntu friendly.

---

### Post by bluedragon436 on 2007-10-29
I know that there is someone on here with your model laptop...I remember seeing it on one of these posts, I will keep looking for it to shoot you a link.  I think for the most part you are in the clear, there is always going to be a few small things to fix up but nothing that you won't find a fix for on here......

---

### Post by Dellfan on 2007-10-29
Regarding the warranty bit. Changing the OS will not void your Dell hardware warranty. The hardware diags are available to run without having Windows installed. They use the same diags to troubleshoot hardware issues on the notebooks loaded with Ubuntu.

Loading Ubuntu will most certainly void/remove any assistance from Dell on software issues (kinda makes sense). Note you get it back if you reload whatever version of whatever OS it was shipped with. Dell supports the OS version they sell you.

They will not support dual boot systems. However, if a software problem shows up under Windows in a dual boot system, and it is not a result of the system being dual-boot they will assist.

It terms of working well, if you pick the correct config it works well. Intel wireless and graphics are your best bet.

---

### Post by bluedragon436 on 2007-10-30
I spoke with Dell about installing Ubuntu on an XPS laptop that I was looking at purchasing and they said that it will void thier warranty as far as software, but not with thier hardware..which is the only thing I am really worried about having covered, but that is just me!!!

---

### Post by fisting_mayfield on 2007-10-30
She's pleased that she can ditch windows -  evidently the off-shore call centre told her that they would assiume any hardware falts would be considered to have been caused by the non-provided software.

As for graphics, she was going to go Nvidia.  Is the Intel better supported?

---

### Post by saru411 on 2007-10-30
nvidia is known for its linux driver support. nvidia is the way to go. as for the intel wireless sure you can go that route but the dell 1390 works just fine with this link([http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390)).

as for the nvidia driver you can just use envy to install it for you([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)). this will pick your video card set up for you making it as easy as click click done. the only configuring you might have to do is your screen resolution(normally envy does this correctly for you also but i remember once having to do it myself). 

in terminal

> sudo nvidia-settings

then goto xserver display configuration, pick the correct settings, then save to x config.

these should be most of your issues.

enjoy your new lappy!

---


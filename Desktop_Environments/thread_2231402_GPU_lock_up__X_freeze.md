---
title: "GPU lock up / X freeze"
date: 2014-06-25
forum: Desktop Environments
---

### Post by jan-bol on 2014-06-25
Hello,

I am experiencing frequent GPU lock ups as mentioned [here ]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze"). I hope I posted this thread in the right section.

**System info**: Ubuntu 14.04 LTS 64 bits on Medion 8822  PC, Intel(R) Core(TM)2 CPU 6400  @ 2.13GHz, Geforce 7650 GS, nvidia  driver version 304.121. See attached lshw file for more info.

**Symptoms**: The freeze mostly happens when I have some  graphical programs open (Inkscape, Gimp, Blender) and then click on the  Unity button (not sure if it's called like this, the top left button in  the main menu). Although I run one or more of these programs most of the  time, so I'm not sure about the reltion with this problems. At one time  I was able to duplicate the freeze a few times by starting blender and  then clicking the Unity button. Now this way of triggering the freeze  does not work anymore.

I also noticed that the "recent opened documents" in Gimp, Inkscape are  erased. Recent documents in Open Office and Blender are not affected

At the freeze my screen starts to flicker randomly although the  flickering responds to mouse movements. The clock (right top corner) is  also freezing. I use ctrl F12, Ctrl F1 and Sudo restart lightdim to get  things up and running again.

**Log info**: I retrieved dmesg.txt and Xorg.0.log. Please find attached. NB: I had to curtail dmseg.txt (removing lots of the "No irq handler for vector" entries) to reduce the file size.

I would very much appreciate your help in this.

---

### Post by jan-bol on 2014-06-30
Hi guys,

Is there anyone who can shed some light on this matter? I  have been searching around, but all I found are mostly instructions on  how to reset the system (x) but not how to solve it. I found [one site]("http://cgit.freedesktop.org/nouveau/linux-2.6/")  that was claimed to be a "solution" on a nouvea related site but there but I'm not sure what I should upload here or what to install and to begin with I'm not sure if it would fix my problem at all.

So if there is anyone who could help me out I would highly appreciate it.

---

### Post by Don_Horsman on 2014-10-18
> **jan-bol said:**
> Hi guys,

Is there anyone who can shed some light on this matter? I  have been searching around, but all I found are mostly instructions on  how to reset the system (x) but not how to solve it. I found [one site]("http://cgit.freedesktop.org/nouveau/linux-2.6/")  that was claimed to be a "solution" on a nouvea related site but there but I'm not sure what I should upload here or what to install and to begin with I'm not sure if it would fix my problem at all.

So if there is anyone who could help me out I would highly appreciate it.

Same result here for searches and the general behavior described. I have accepted the fact that I may have to reset the system a couple of times each day when 14.04 LTS locks up.

My hardware is several years old, so I'm considering upgrading even though my machine has all the capability I need if it were not for the annoying OS lockups. Oh well, that local landfill needs more trash to fill it I guess. :(

---


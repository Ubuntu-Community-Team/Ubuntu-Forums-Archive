---
title: "Dell E6400 problems"
date: 2009-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gabox01 on 2009-01-27
Hi!

I have recently bought a new Dell E6400 laptop, and have many problems with Ubuntu (Interpid)

The three most important issues are:

-2D/3D performance is really slow, glxgears does 300 FPS. I think my Intel 4500HD card is not recognized.

-suspend/resume is broken. Sometimes the maschine can't return from suspend, all i can see is a frozen login window. This happens nearly 5 times out of 10 tries.

-trackpoint is not working correctly. sometimes it jumps randomly to the edges of screen.

Can you please help me to resolve these issues?

---

### Post by Gabox01 on 2009-01-29
up

---

### Post by moody_mark on 2009-01-30
Hi, I just received a Dell E6400 through my work and will be sticking 8.04 on it tonight. If its any help, i'll let you know here how I get on. If its working ok, it might be worth you dropping back to 8.04.

---

### Post by moody_mark on 2009-01-30
Ok, im all installed and up and running on the E6400 on 8.04. The CD I do my initial install from is from August last year so initiall my wireless didnt work, but I always install with a hardwired connection and after I'd done all the updates I noticed that I got prompted to install a restricted driver.

If theres any tests you want me to run to verify against on 8.04 let me know. All the usual stuff like sound and compiz are running fine.

---

### Post by psych on 2009-01-31
Hi,

I have a Latitude e6500... with Intel graphics.
Switching from EXA to UXA solved the performance issues for me (in intrepid you have to add xorg-edgers ppa i think)... the standby problems are fixed by upgrading to kernel 2.6.28 or in Ubuntu 9.04 Alphas ...

For brand new hardware the latitude series is supported really good i think. 
Intrepid works perfectly with a little bit work... and it should run perfect out of the box with Ubuntu 9.04 Jaunty.

---

### Post by smaw0351 on 2009-02-04
> **psych said:**
> Hi,

I have a Latitude e6500... with Intel graphics.
Switching from EXA to UXA solved the performance issues for me (in intrepid you have to add xorg-edgers ppa i think)... the standby problems are fixed by upgrading to kernel 2.6.28 or in Ubuntu 9.04 Alphas ...

For brand new hardware the latitude series is supported really good i think. 
Intrepid works perfectly with a little bit work... and it should run perfect out of the box with Ubuntu 9.04 Jaunty.

I also have an E6400 with the Intel 4500MHD card running Intrepid. I am also having the video performance issues. Could you post your XORG so I can see what I need to do to switch from EXA to UXA? attached is my xorg.conf

---

### Post by rasmus91 on 2009-03-13
> I also have an E6400 with the Intel 4500MHD card running Intrepid. I am also having the video performance issues. Could you post your XORG so I can see what I need to do to switch from EXA to UXA? attached is my xorg.conf

Can you tell how to change EXA to UXA, i've heard warnings about UXA being to unstable, but if it will solve the performance problems for GMA 4500 MHD im in!

---

### Post by smaw0351 on 2009-03-13
i've just given up and stuck it out with the default driver and xorg. my FPS is still between 100-200.

hopefully a fix will come soon or maybe it'll be better with jaunty. i can still do everything i need to. compiz works fine, virtualbox, etc. so everything besides playing 3d games.

---

### Post by rasmus91 on 2009-03-14
Okay, installed 9.04 alpha.

performance problems solved: i get 1130+ fps with the GMA 4500 MHD

---

### Post by douglas_slac on 2009-04-07
I got this laptop yesterday, and I installed the Ubuntu 9 alpha on it, and mostly it worked fine.  The suspend/resume didn't work until I installed the nvidia drivers, and now it works.  Doesn't work with the 'nv' driver.

Now I'm having a problem that the sound doesn't work at all.  I don't get any errors, it just doesn't work.  What should I be looking for here?  It looks like I need the snd_hda_intel kernel module to work?  This module wasn't getting loaded at boot, so I forced in /etc/modules, and now it is loaded.  Still no sound.

Not sure what to look for here.

---

### Post by douglas_slac on 2009-04-07
Ok, looking at other posts, it turns out that the sound is low on this machine for some reason.  If the mixer levels are below 50% then the sound in muted.  I've not maxed out all levels, and the sound is ok, still maybe a little quiet, but it is there at least.  So, the sound does work, it is just quiet, and easily appear muted.

One thing, when using headphones, this turns off the main speakers, which is fine.  The "headphone" sound level doesn't do anything though, and to control headphone volume you use the main mixer level.

---

### Post by cix on 2009-05-07
> **rasmus91 said:**
> Okay, installed 9.04 alpha.

performance problems solved: i get 1130+ fps with the GMA 4500 MHD
Great! Would you please upload your xorg.conf? Thanks a lot!

---

### Post by cix on 2009-05-08
The following section solved the problem for me.
If you have enything better, please let me know...
---
Section "Device"
    Identifier  "Intel X4500MHD"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
    Option        "DRI" "true"
    Option        "AccelMethod" "uxa"
    Option        "MigrationHeuristic" "greedy"
EndSection

---


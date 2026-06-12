---
title: "8800 GTS driver issues"
date: 2009-01-04
forum: General Help
---

### Post by Chinzo on 2009-01-04
Hello all,
I decided to install Ubuntu (8.10) for my first time yesterday so I am very new to Linux.

My problem is that I cannot seem to enable any visual effects from the visual effect menu, if I try to change it to normal or extra is says I cannot enable them, leading me to believe I don't have the correct driver but the generic driver runs video and at the native resolution of my monitor. When I try to open the NVIDIA X driver utility thing it says I am not using one. 
I have tried each of the 3 drivers suggested by Ubuntu (173,96 and 177(recommended) I think)but when I activate any of these 3 it starts up in Low quality mode and gives me an error about failing to initialize the NVIDIA device.

I am running an NVIDIA 8800 GTS
Notes:
-My software is up to date
-I tried using EnvyNG but to no avail
-all of this on a fresh install of 8.10

Help please, it seems like this should be something easy to fix but I can't figure out what I'm doing wrong. Remember, I am totally new to this and will probably need to be walked through the process. Thanks in advance for any help.

---

### Post by Chinzo on 2009-01-04
Bump

---

### Post by Chinzo on 2009-01-04
Still nothing, HALP!

---

### Post by Chinzo on 2009-01-15
bump

---

### Post by hyper_ch on 2009-01-15
you could try the 180.06 driver instead... works IMHO a lot better... the 180.22 driver gave problems on 8.10:  [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by Chinzo on 2009-01-17
I couldn't find 180.06, it always suggested 180.22 but I didn't try that one yet so I tried to run it and it won't let me, when trying to run it through terminal it said "sh: Can't open NVIDIA-Linux-x86-180.22-pkg1.run" 
I have a question though: after installing any driver, am I supposed to do something else? Like configure something with the X server? I am completely new to this so I'm just guessing.

---

### Post by ushimitsudoki on 2009-01-17
Chinzo,

I have 2x8800GTS 512 in this box and run the 180.22 drivers currently.

Here is my suggestion:
Download the drivers from Nvidia and follow this thread to install them:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

You will have to chmod +x to the driver download so that you can execute it.

As part of the install, you will be asked if you want the program to try to configure X for you. Say yes at first. After you have X working, in the future, don't do this again. You only really need it configured once - a driver update is not a reason to change xorg.conf and you don't want the driver install program to overwrite changes you might make for other reasons.

You will be doing this from the REAL command line, with X not running. You might want to use GRUB to boot into "recovery mode" to do this from. The driver install will warn you that you are installing as root, but everything will work fine like this.

The hard part I found was getting all the Ubuntu restricted-extras/envyNG/vesa stuff out of the way so I could actually get the downloaded drivers installed. Expect this to be the majority of the hassle.

Once the drivers are installed, you will have to re-install them if your kernel changes. It's no big deal, because once you get them installed the first time, subsequent installations are just a matter of running the script. Just keep the drivers on your hard drive - don't delete the install script when you are done.

Once you get X up use "gksudo nvidia-settings" to configure it further. Again, you will have the option to save to /etc/X11/xorg.conf. In this case, you'll usually want to save, because you will be making resolution changes or whatever. 

Unless you are messing about with changing number of monitors/x sessions/resolution - this is basically a "once you get it right the first time, it's no problem" situation.

That first time can be a pain in the butt, though.

---

### Post by Chinzo on 2009-01-17
thanks a ton ushimitsudoki, I will give it a shot.

---


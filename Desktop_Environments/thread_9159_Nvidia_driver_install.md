---
title: "Nvidia driver install"
date: 2004-12-24
forum: Desktop Environments
---

### Post by Sapper2ID on 2004-12-24
I don't know  where to enter the commands to install the drivers. I'm very new to PCs as you can tell.

---

### Post by sicness86 on 2004-12-25
[QUOTE=Sapper2ID]I don't know  where to enter the commands to install the drivers. I'm very new to PCs as you can tell.[/QUOTE]
 Applications->System Tools->Terminal
and follow:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by Sapper2ID on 2004-12-25
All went well with the commands, that's what it said. Now i can't get the linux os up at all. It can't start  graphics at all, either on internal  or pci. I'll have to reinstall just so I can see it. Any ideas?

---

### Post by sicness86 on 2004-12-25
Post your Xfree86 log (/var/log) and your xfree config (/etc/X11/XF86Config-4).  Might be able to see whats wrong.

---

### Post by Sapper2ID on 2004-12-25
I can't even get into that os the way things are. I'll try reloading (for the 6th time) and see what happens. I'll be back

---

### Post by Dylanby on 2004-12-25
$ sudo nvidia-glx-config enable <= Didn't work for me.

I used the "BinaryDriverHowto" on the Ubuntu wiki, adding to my etc modules using:

$ sudo nano /etc/modules

(After the "$ sudo dpkg-reconfigure xserver-xfree86" step)

But I still couldn't get into X until I installed the linux-restricted-modules for the appropriate kernel.

$ sudo nano /etc/apt/sources.list

(& uncomment out "universe")

---

### Post by Sapper2ID on 2004-12-26
This would replace the 3rd line in the install set? Whats wiki?, etc modules? I meant it when I  said I was very new to command line stuff and pcs in general. Anyone care to second this idea. No offense, I'm getting tired of installing this thing. How would I save and post the start up log?

---

### Post by Dylanby on 2004-12-26
When I installed Ubuntu on my current system I was dropped at the cli. Seeing as I was there I decided to install the nvidia drivers.

This is what I did after logging in at the command line:
=>"sudo nano /etc/apt/sources.list" & uncommented out (deleted the '#' from) the 'universe' line.
=>"sudo apt-get update && sudo apt-get upgrade"
=>"uname -a" will tell you what kernel you have installed. You have to install the corresponding restricted modules.
=> e.g.: "sudo apt-get install linux-restricted-modules-<your kernel version>"

I then installed the Nvidia drivers using the howto at this page for reference:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)
(The 2nd group of 5 steps under the Nvidia section).

At this point I was able to start X.

Disclaimer: I'm new to Linux myself so take my experience with a grain of salt.

---

### Post by Sapper2ID on 2004-12-26
The honesty is great. I'm doing this to learn and learning usually involves some smoke and funny burning smells, lol. I'd like to never give M$ any more of my money someday. I'll try what I did before, if that doesn't work I''l try it your way. I'll post the  results. Thanks, Sap.

---

### Post by Dylanby on 2004-12-27
Also, with the steps I listed above there was some trial & error involved...it wasn't done in one smooth episode.

For example, at first the horizontal & vertical scan ranges for my monitor weren't setup properly & I received the "no screens" error. You can change these during "step 2" in
the part of the howto I linked to when you do "sudo dpkg-reconfigure xserver-xfree86".
I used Google & typed "<my monitor brand> <model#> horizontal scan range" to find the info.

One last thing, you can type "sudo dpkg-reconfigure fontconfig" & turn on the auto-hinting for better looking (IMHO) fonts in X.

Good luck!

---

### Post by Sapper2ID on 2004-12-27
Now, do I do this in the Terminal in Applications or do I enter this in the recovery mode?

---

### Post by Dylanby on 2004-12-27
Well, if you are in X/Gnome you can use the terminal. I did all my steps (except the fontconfig) before I was in X. I haven't used the recovery mode yet.

For the fonts you will have to complete their configuration from within Gnome to get the benefit of smoother fonts.

Computer => Desktop Preferences => Font

Then adjust your settings for font rendering.

If you're in X/Gnome you can also install the packages you need for the driver installation from Synaptic. Then use the terminal to do the finishing steps. It's probably easier to do the whole thing from the terminal.

---

### Post by Sapper2ID on 2004-12-28
Problem Solved!
 I found xserver needed to be changed to use PCI slot 1 (my card). Thanks Dylanby for the direction to reconfig. This was my 15th time loading unbuntu and was about to be my last. I learned a lot screwing this up. I still haven't found any access to nvidia adjustments but I will.

---


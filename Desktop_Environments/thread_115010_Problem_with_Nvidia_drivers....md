---
title: "Problem with Nvidia drivers..."
date: 2006-01-09
forum: Desktop Environments
---

### Post by Fixxxer on 2006-01-09
Hi! I'm new to these forums and a have a couple of problems...
The first problem is that I can't get any other nvidia driver to work except 81.74, and those give me a (slightly) flickering cursor. Every other driver just gives me a blank screen.

The second problem is with framebuffer, I'm using vga=792 in menu.lst but it's only working if my monitor is connected with a vga connector. When using dvi I get the error "you passed an undefined mode number".

Thanks in advance!

---

### Post by leech on 2006-01-09
Are you using Breezy?  The nVidia drivers in that are 7667 and worked great for me, if you just use the ones that are in the repositories.  Just run from the terminal ```
sudo apt-get install nvidia-glx
``` Sounds like you've already changed the driver in /etc/X11/xorg.conf.

Leech

---

### Post by Fixxxer on 2006-01-09
Thanks for your quick reply! Forgot to mention that I'm using th k7 kernel...

---

### Post by Fixxxer on 2006-01-10
Anyone?

---

### Post by r4ik on 2006-01-10
Try,

sudo nvidia-glx-config enable 

If you got the 7667 and after the sudo Leech gave you.

Good luck.

---

### Post by Fixxxer on 2006-01-10
Ok, got the official 81.78 drivers working (needed to install linux-image-k7), any suggestions on the framebuffer problem?

---

### Post by Fixxxer on 2006-01-11
bump

---

### Post by Fixxxer on 2006-01-14
Ok this is weird, it turns out that I also have to use the vga connector in order for the drivers to work. Using dvi just gives me a blank screen. Any clues what the problem could be?

---

### Post by Fixxxer on 2006-01-15
Is there really no one who can help?

---

### Post by ajkeys on 2006-01-31
Bumping, because this is an issue that got buried and unanswered or if it did a link would be nice. :D Also solidandshade is having the same problem in this [thread]("http://www.ubuntuforums.org/showthread.php?t=115918").

---

### Post by ddtmsa on 2006-01-31
[QUOTE=leech]Are you using Breezy?  The nVidia drivers in that are 7667 and worked great for me, if you just use the ones that are in the repositories.  Just run from the terminal ```
sudo apt-get install nvidia-glx
``` Sounds like you've already changed the driver in /etc/X11/xorg.conf.
[/QUOTE]

This post contained all the information I needed to get my Nvidia card to work, I have found no need to update my drivers beyond the 7667 ones in the repositories. Yes, perhaps you may need to use the absolutely latest updates for the drivers to get them working with Windows, but within Ubuntu the 7667 ones are both stable and supported. That means that if you install and use these drivers as described you will have no problems what-so-ever. 

Ubuntu is not windows! Newest equals most unstable in Ubuntu, as opposed to Windows which is always just trying to keep up with all its weaknesses!

As a general reference take a look at [http://ubuntuguide.org/](http://ubuntuguide.org/) (originally written for the previous release but still relevant) which includes information on getting nvidia graphics cards to work.

---

### Post by ajkeys on 2006-02-15
[QUOTE=Fixxxer]Ok this is weird, it turns out that I also have to use the vga connector in order for the drivers to work. Using dvi just gives me a blank screen. Any clues what the problem could be?[/QUOTE]
I know I am bringing up an old thread, but with the nvidia drivers in order to use the dvi port you have to use
```
Option          "ConnectedMonitor" "DFP"
```
under the device section.

---


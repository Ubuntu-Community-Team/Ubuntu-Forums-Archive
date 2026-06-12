---
title: "nVidia Questions"
date: 2006-04-13
forum: Desktop Environments
---

### Post by Mr Egg on 2006-04-13
I'm about to install Ubuntu, but before I do I need to know, will the GUI work right away without any drivers? I'm using an nVidia GeForce 4 Ti 4200 with AGP8X. I'm absolutely new to Linux and I know virtually nothing about it.

---

### Post by zubrug on 2006-04-13
I do not think the gui will work after install, you will have to do a 
sudo dpkg-reconfigure xserver.xorg
Pick the vessa driver, you can most likely just hit enter for the rest except you should know the bus id of your graphics card (mine is 2:10:0) untill you are back at the command prompt. 
sudo reboot
Once you get your gui you can then install the glx nvidia drivers from synaptic or use automatix.

---

### Post by Mr Egg on 2006-04-13
How do you find the Bus ID of your graphics card, right now I am using Windows XP Professional.

Here is the information I know about it so far:
Graphics card information:
  Processor: GeForce4 Ti 4200 with AGP8X
  Video BIOS version: 4.28.20.05.11
  IRQ: 16
  Bus: PCI
  Memory: 128 MB
  ForceWare version: 81.98
  TV Encoder Type: Philips 7104

---

### Post by zubrug on 2006-04-13
It has been a while since I used windows so I will attempt to remember what I am thinking about.

look in control panel for a hardware icon, open it and look for your card.

---

### Post by Mr Egg on 2006-04-14
Will the Live CD operate the same as the install CD?

---

### Post by Mr Egg on 2006-04-14
I am currently running the Live CD (I'm posting this message from it). Anyway, the GUI worked as soon as it booted, and it also detected my wireless card and its working without a problem. Will this be the case when I use the Install disc to install it onto my hard-drive?

---

### Post by Sutekh on 2006-04-14
The LiveCD and Install CD experience translated pretty much perfectly for me. 

Your mileage will vary, but I think its a pretty safe bet that things will work.  

Also just wanted to address this question...
[quote=Mr Egg]will the GUI work right away without any drivers?[/quote]When you install it will install drivers for your video card.  Whether or not they are a best fit remains to be seen.  You may need to change the driver to vesa (as zubrug said) to get the GUI working, but seriously it shouldn't be too hard for you.

---

### Post by mrchrisblau on 2006-04-14
I'm running an nVidia card aswell and X worked for me right out of the box.

However, it worked at an ugly resolution. 

To fix this I had to install the latest nVidia drivers. Here is a great howto on installing them: [http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers)

---

### Post by Mr Egg on 2006-04-14
Thanks everyone. I'm gonna finish backing up my PC then I may install it on my hard-drive.

---


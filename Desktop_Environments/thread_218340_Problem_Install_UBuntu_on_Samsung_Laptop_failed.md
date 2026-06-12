---
title: "Problem: Install UBuntu on Samsung Laptop failed"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Muhlaulla on 2006-07-18
Hi,

i can't find a similiar Thread, so i open my own (sorry, if someone has same probs an i didn't see it).

My Problem:

I want to install Ubuntu on my Samsung R50 Laptop.

Specs:

1,76 Ghz Intel Centrino
1GB DDR2 Ram
80 GB HDD
ATi X700 Mobility with 128MB Video RAM (not shared)

So, i downlaoaded the Ubuntu Desktop Live CD and boot. I choose Start and Install Ubuntu. My native Screen Size is 1280x800 but i cant select it, so i try 1024x768.

Ubuntu loads everything an then i only see a Black Screen. I hear the start sound, but i can see nothing. So i connect my TFT via VGA out, but i still get no signal.

So i tried it 3 times, but every time its the same problem. What can I do?

Sorry for my english, its not very good :)

---

### Post by asplode on 2006-07-18
You could try option 2 on the live cd (safe graphics mode), just to get it installed.  Once its on your computer, look at [this guide]("http://ubuntuforums.org/showthread.php?t=204910&highlight=ATi+X700") to see how to set up your ATI videocard.

---

### Post by TheMindField on 2006-07-18
This is definitely a video card issue.

You need to find a guide tailored to your system for ATI setup. 

You can also try changing your video card settings in BIOS.

As soon as you start your system, you may see thing that says "press this key to setup system/BIOS"

Press that key, then navigate to your video card options.

Change it from Sideport to Sideport + UMA and put shared system memory as "128 mb".  Save and reboot into Ubuntu.

---

### Post by Muhlaulla on 2006-07-18
Ok , thank you. I will try it!

---


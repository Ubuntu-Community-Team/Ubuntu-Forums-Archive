---
title: "Saitek P2600 and Minecraft"
date: 2014-06-18
forum: Gaming &amp; Leisure
---

### Post by dannyboyinpy on 2014-06-18
I have a Saitek P2600 game controller and am wondering if it would be possible to use it with minecraft. I would be extremely happy to have some step by step intructions. I have no drivers installed for it yet. I am running Ubuntu 14.04 (Trusty). Thanks in advance!

---

### Post by oldrocker99 on 2014-06-18
If you use Synaptic or the Ubuntu Software Center, and search for **joystick**, you'll see several programs that will help you out. It's almost certain that the Saitek P2600 is supported by the kernel; you just need to translate joystick signals into keypresses for those games that require that, and calibration tools, etc.

Seriously, the search function isn't bad at all, and you can often find just what you're looking for.

---

### Post by dannyboyinpy on 2014-06-18
I tried what oldrocker99 said and installed joy2key, the only thing I could find, and I cannot get it to work. Also I don't think it will do mouse simulation, which I also need. Thanks anyway. :/

---

### Post by dannyboyinpy on 2014-06-18
I have now also tried qjoypad and it doen't seem to recognise that i have a controller at all

---

### Post by xREDEMPTIONx on 2014-06-19
The first thing I would do is install jstest-gtk from the repositories. Start it up and verify your controller is working. If so you should see the controller and then hit "properties" and verify that all buttons and axis are working. If yes then I recommend the program antimicro for setting up a config for Minecraft. There are debs available for ubuntu here- [http://www.ryochan7.com/projects/antimicro/](http://www.ryochan7.com/projects/antimicro/) 
I have made configs for Minecraft using antimicro for my DS3,DS4 and F710 controllers and its works beautifully!

---


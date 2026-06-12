---
title: "Little problem with OpenGL"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by mu:te on 2007-06-04
So here is the thing!

When ever I try to open WoW with wine or any other Sim by using the following command "-opengl" I always get "world of warcraft was unable to start up 3d acceleration" but when I don't add the command I just have less than 2fps in the game! :/ 

Can anyone help me fix this?

---

### Post by Ferrat on 2007-06-05
I bet you, you don't have any 3D drivers installed or atleast not active. 

type this in a terminal 
glxinfo |grep direct

What grafic card do you have? 
What drivers have you installed?

---

### Post by mu:te on 2007-06-05
I got

> direct rendering: No


So no I probably dont have any driver at all, but do you think that you might help me to install one since I've been having troubles installing drivers on my own..

When I formated the computer, I wen't to restricted drivers and downloaded the Ati Driver. I was able to open World of Warcraft with a lot of FPS, the game was very smooth but the computer always crashed 5sec after gameplay.

Than I tried the ATi driver that ati.com provides, when I tried to open world of warcraft with that driver I just got this error message.  "world of warcraft was unable to start up 3d acceleration"

I'll give you every info that I believe that you'll need to know to help me sort this out.

IBM ThinkPad T43
Processor: Intel  Cetrino 1.83Ghz Mobile Technology
Graph Card: ATi Radeon x300 64MB
Memory: 1.5Gb Corsair 677Mhz

With this hardware I could get up to 80fps stable on Windows.

I doubt that you'll need to know whats inside my xorg config file since I don't have any driver installed.

---

### Post by Ferrat on 2007-06-05
Try this HowTo out =)

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---


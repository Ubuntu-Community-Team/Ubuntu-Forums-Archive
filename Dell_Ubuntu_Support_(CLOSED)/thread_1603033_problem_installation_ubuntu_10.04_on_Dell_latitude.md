---
title: "problem installation ubuntu 10.04 on Dell latitude E4310"
date: 2010-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by etienne.mon on 2010-10-22
Hello,

I am quite a beginner in ubuntu. I am sorry to post such a thread but I did not find a solution.
I bought an Dell Latitude E4310 with video card intel GMA HD.
When I start ubuntu 10.04 on a usb key not problem eth0, wifi and even the integrated webcam works!
Then I decide to install it on the whole disk. Everything was ok, but when I restart I get a black screen and I hear the little music that means that I am on the login window. 
What is really funny is that if I put an externa screen on the VGA port, it is detected so that I can do everything on this external screen. 
The amazing thing is that if I remove the plug, the internal screen of my labtop works fine and I can do everything without any problems...
Is there any way to get the internal screen be detected by default ?

I also try the i915.modetest=1 in the grub like [http://ubuntuforums.org/showthread.php?t=1545741&highlight=dell+E4310](http://ubuntuforums.org/showthread.php?t=1545741&highlight=dell+E4310)
 I am quite lost.
Etienne

---

### Post by gibbylinks on 2010-10-22
Have you tried just "nomodeset" ?

---

### Post by etienne.mon on 2010-10-22
> **gibbylinks said:**
> Have you tried just "nomodeset" ?

It is worst because it crashes. I should turn off with a long presure on the power button.

---

### Post by etienne.mon on 2010-10-22
I have found this
on the grub, you edit and change "quiet splash" by "nomodeset single". Then it strarts with some menus like repair mistakes
connect with basic graphism
...
You choose connect with basic graphism. At the end the grahism is ok and everything is fine.
Then I have made this change permanent on my grub so that everytime I start the computer, I should click on two menus to get the correct login windows, it is not a nice solution
anyone has a better one ?

---


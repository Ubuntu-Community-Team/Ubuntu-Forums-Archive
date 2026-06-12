---
title: "Ati 9800 Pro"
date: 2005-10-27
forum: Desktop Environments
---

### Post by BlackWingAngel on 2005-10-27
Hi, i've installed the ubuntu breezy 5.10 but my video card(ATI RADEON 9800 PRO) I can't go over 1024x768 of resolution and 60hz of refresh frequence of the monitor.. why??
the card works very well and it isn't damage 
thanks

---

### Post by tmadsen on 2005-10-27
seen this? [http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+howto]("http://ubuntuforums.org/showthread.php?t=75378&highlight=ati+howto")

---

### Post by Morrigu on 2005-10-31
I had to unplug my TV-out connector to be able to change resolution and refresh rate. Otherwise fglrx would just detect the max values of TV instead of my monitor.

---

### Post by j0eb0b on 2007-08-31
I am trying to change the resolution of my 9800 Pro using the following command:

sudo dpkg-reconfigure xserver-xorg

Now for today's Noob type question.  When I get to the screen that tells me to delete any screen resolution that I don't want to use how do I select them?  The only keyboard keys that seem active in the panel are tab (which highlights OK) and enter which takes me to the next panel.  

As further background, this machine was originally built with an nVidia fx5500 and I added the 9800 Pro recently.  After I put the 9800 Pro in I installed the ATI driver via Automatix.  How can I verify which ATI driver version I am running?

Joe

---

### Post by OlympicSoftworks on 2007-08-31
Use the arrow keys to move up and down the list and spacebar selects.  You want to highlight all the resolutions that you want to have available, it will start on the highest of them when you boot again.

---

### Post by j0eb0b on 2007-08-31
Thanks,

It never occurred to me that the keyboard would select.  All is now right with Feisty.

---

### Post by j0eb0b on 2007-08-31
Try that again, it never occurred:KS to me that the space bar would select.[http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---


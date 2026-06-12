---
title: "Ubuntu 18.04 keeps opening random windows intermittently"
date: 2018-10-04
forum: Desktop Environments
---

### Post by vkidubu on 2018-10-04
Hello,

I'm a long time Ubuntu user and recently upgraded to 18.04. I notice that sometimes by click and drag gets stuck in the "on" position. When this happens and I use Spyder to code python then any mouse movement selects (even without clicking) and in Filemanager if I click on a favorites folder it tries to move it. I can't quite figure out what starts it and usually, a reboot fixes it, only to reappear intermittently. 
From time to time the mouse seems to go to the top left corner and many of my shortcut programs start opening. This too I can only fix with a reboot. 

I tried to switch from Synaptics touchpad driver to libinput but that seemed to increase of the random programs opening problem even more. I just switched back to Synaptics. I am not quite sure what else to try. 
Seems to happen a lot when I come back from screensaver screen lock mode.

Appreciate any help. The last thread I saw with random windows opening was from 2011 with versions 9 to 14. 
I'm on an Asus laptop with gnome desktop extensions. Have a touchpad for a mouse and have 2 monitors connected.

Update.   
I think I found the source of this problem and fixed it.   It's been working for 2 days.   This is related to the touchscreen which was causing the mouse/ touchpad to seem to act erratically.   I followed the instructions in the post below and completely disabled the touchscreen.  Just doing "xinput disable  <touchscreen_id>"  did not do the trick.  

[https://askubuntu.com/questions/1038248/how-to-disable-touchscreen-permanently-on-ubuntu-18-04](https://askubuntu.com/questions/1038248/how-to-disable-touchscreen-permanently-on-ubuntu-18-04)

---


---
title: "Jaunty - touch pad not moving the mouse"
date: 2009-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Alarion Irisar on 2009-04-25
I've installed Ubuntu 9.04 (Jaunty) on my Dell Inspiron 1720 Notebook (and Kubuntu Desktop, for that matter). It all worked well until yesterday, when I noticed that my touch pad did not move my mouse any longer. 
I can click and Ubuntu will notice it, but I can't move the cursor with the touch pad. I've tried switching it on and off in the settings (I've downloaded a package that added a separate Touchpad entry under the System settings), and I've also tried changing the sensibility. It doesn't help to unplug or plug in the USB Mouse I'm using, either. And under KDE it's the same situation.
I'm at a loss here. The touch pad buttons do work, it is fully recognized and it worked before. 
Anyone got a good idea what to change so it works again? I'm kind of a novice, so if it's more advanced than using a packet manager it would be really nice if you could provide me with the necessary bash prompts.

Thanks a lot in advance
Alarion

---

### Post by warr85 on 2009-04-25
I have the same problem but from the beggining... i just installed ubuntu 9.04 yesterday and every thing works fine, exept for the touchpad. how can i make it work...???? thanks in advance.

---

### Post by V_jeroen on 2009-04-27
Yup , I have also the same problem.
FOr me th etouchpad is not enabled or installed because in my log files I can't find an error. 

Regards

Jeroen

---

### Post by duckfeet on 2009-04-27
I had many problems w/my touchpad, similar to what has been posted, and here is the thread which really helped me...my main problem seemed to be not having "SHMConfig" set to "on" or "true" in input devices, I believe...I also had to reboot, to put it into effect, (I know it was for earlier OS, but I have 8.04)anyway:



[http://ubuntuforums.org/showthread.php?t=230197&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=230197&highlight=touchpad)

---

### Post by kbailey on 2009-04-28
I had the same problem on an Averatec laptop. The following fix worked for me, though it needs to be issued as an update so others don't have this problem. It's certainly not good for newcomers to Ubuntu.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33")

---

### Post by Alarion Irisar on 2009-04-29
Hey, that hint worked great and was really easy to perform. Thanks a lot, now I can use Ubuntu again. :-)

---


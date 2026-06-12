---
title: "Ubuntu now boots up to tty instead of gui"
date: 2005-12-14
forum: Desktop Environments
---

### Post by futz on 2005-12-14
I have no idea how I managed it, but I've broken my Ubuntu. 

I first discovered the problem when stupid Amarok crashed yet again and totally locked the machine up. I hit the reset button and now it starts up in tty1 instead of the normal gui. 

I can log in to tty1 and type startx and use the gui normally, but even after a complete shutdown and restart, it seems it aint comin back without some help.

Any ideas?

------------

2nd topic: Anyone notice that Amarok crashes a LOT when you have a big collection? I only had around 1000 songs or so for quite a while, and had no major problems with Amarok. But I recently moved a bunch of tunes over from one of the XP boxes. There's now around 4300 songs in the playlist and Amarok crashes all the time now.

---

### Post by RAOF on 2005-12-14
I'd try "sudo dpkg-reconfigure gdm".  That should set up the graphical-login thing again.

---

### Post by futz on 2005-12-14
Now this is interesting. Here's what I get when I do "sudo dpkg-reconfigure gdm":
```
/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed
```

EDIT: I just went to Synaptic and looked for gdm. It's not installed. Should it be?

---

### Post by anil_robo on 2005-12-14
gdm is graphical device manager (or something similar I remember). It's absolutely essential to have GDM before you can start X normally. Alternatively, if you're able to go in text mode, why don't you login from the text mode, and then try startx command? Once you're logged in, gdm is not required I feel.

---

### Post by futz on 2005-12-14
I've got it fixed. Reinstalled gdm and Synaptic warned me that it was going to remove gnome-audio and ubuntu-sounds. Apparently when you install gnome-audio and/or ubuntu-sounds, gdm gets removed. I should probably disable a couple of those funky repositories, I guess.

Thanks for the suggestions guys!

---


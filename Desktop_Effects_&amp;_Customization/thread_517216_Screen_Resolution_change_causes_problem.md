---
title: "Screen Resolution change causes problem"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by Orc65 on 2007-08-04
I recently upgraded my monitor and have altered my screen resolution to 1680 X 1050.
Looks great, however there were some differences in the way windows appear, I don't have the min,max and close buttons in the top right anymore, they seem to have just disappeared. 
(no big deal)
My main problem is with the terminal, it now appears as a blank white box, no visible text, although it is apparently still there, just not visible. Changing the screen res back to 800 X 600 does not change the terminal. Had a look in the Xorg.conf and 1680x1050 is not listed as a mode. 
Can someone give me clue as to how I should go about sorting this problem out. While your at how do I access a folder as root, I appear to have several xorg.conf files, If I find the original and get rid of the extra conf files I could start over?

---

### Post by agds on 2007-08-04
You might want to try
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you a bunch of questions, as though you were installing the X server for the first time.  This will back up your current xorg.conf before it changes anything.

If you want to try an older xorg.conf, you can list the contents of the directory like so:
```
sudo ls /etc/X11
```
I would *not* recommend deleting any of the files you find there.  Rather, if you want to try an older file, back up what you have and overwrite xorg.conf with the older file.  For example,
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo cp /etc/X11/xorg.conf.20070726110232 /etc/X11/xorg.conf
```
would back up the current config to xorg.conf.bak and then overwrite it with the one from July 26.

---

### Post by Orc65 on 2007-08-05
Thanks for the reply, I did manage to fix it on my own, I'm not exactly sure how but I'll explain what I did.
I tried the nv driver and discovered that my Terminal had visible print so I ran "sudo dpkg-reconfigure -phigh xserver-xorg", whilst in the GUI, then selected the nvidia driver and everything returned to normal.
I had tried this command before, but in safe mode after restarting, due to my screen being unusable after altering the resolution. Also after I set the driver and resolutions wanted it took me back to the command line and as n00b I did not know the command to restart the system so I hit the restart button on the tower. This is probably where I went wrong in the first place.

Thanks again for the reply

---


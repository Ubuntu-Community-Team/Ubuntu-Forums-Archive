---
title: "White/Beige/Brown/Black Screen of Death"
date: 2009-03-15
forum: General Help
---

### Post by snoopers on 2009-03-15
I'm new to Ubuntu. I'm trying to build an HTPC with MythTV  and experience all the pain and gain... without Mythbuntu. I have the following setup:

Motherboard: M3N78-VM (NVIDIA GeForce 8200 on board)
NVIDIA Driver Version: 180.11
OS: Ubuntu 8.10

What happens is that every once in a while (completely random times) the screen will lock up. It will either lock up White, Brown, Beige or Black. A solid color. 

I have done the following:

1) Reset and gone to Safe Recovery and done either (neither worked):

Fix X
 
or 

nvidia-xconfig

I have also updated the drivers to 180.11

I have tried crtl+alt+F1, CRTL+ALT+BKSP, and any other CRTL+ALT combinations I can think of. I have no clue why this is happening.

As a caveat, the error is more likely to occur and occurs more frequently when I have the HDMI (on-board too) plugged into my TV. Otherwise, it happens less frequently (but still annoying) when it is plugged into a monitor (DVI on-board).

Any help would be appreciated. I have read the posts and tried what they all say, but no luck so far.

Thanks.

Sam

---

### Post by martrn on 2009-03-15
You might need to change your screen resolution. Start in a terminal and edit your xorg file by : 

sudo nano /etc/X11/xorg.conf

There will be an error message from the Xorg  X11 server at /var/log
```
ls /var/log/  -la
less /var/log/Xorg.0.log
```
(the .0.log might be .1.log, .2.log etc....

It might tell you what the error is, and would be helpful ?

If it happens a lot it might be helpfull to look at /var/log
for error logs.

---

### Post by snoopers on 2009-03-15
Thanks. I did look at the log file. I don't really know what I'm looking at though. I tried to remove the glx according to this post [here]("http://ubuntuforums.org/showthread.php?t=834773&highlight=white+screen+of+death+nvidia") but that didn't seem to work either.

---

### Post by LiamWilson on 2009-03-15
try this in the terminal:

```
sudo apt-get remove compiz
```

That worked for me.

---

### Post by snoopers on 2009-03-15
I ran that in Recovery Mode and then logged in and the screen went beige.

I also ran 
sudo apt-get remove compiz compiz-core

and I still got the Beige Screen right after log in. I guess I'm making progress, from white to beige. I have a feeling that it is an issue with something that is loading at startup but I have no clue what it is. (I could also be wrong... I do come from Windows and I'm new to Ubuntu.)

---

### Post by 2rB on 2009-03-15
I had the problem with the all white screen after log on - after changing from nVidia to ATI-card.

However - I could se the window-edges of the autostart-programs "behind the white screen" if I for example did an alt + tab.
I also had my mouse-cursor pressent at all times.

Removing compiz as suggested in this tread solved it for me.

This probably wont help you - but ment more as a "guide" to future people entering this problem - and a thanks to those fixing my problem.

---

### Post by snoopers on 2009-03-31
I tried to install MythBuntu instead and I got the same error. I really think it has to do with either the Hauppage Card or the Video Card on Board the Motherboard. I guess I'll have to do more testing...

---


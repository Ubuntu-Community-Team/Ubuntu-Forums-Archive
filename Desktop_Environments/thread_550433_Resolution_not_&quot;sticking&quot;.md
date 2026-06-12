---
title: "Resolution not &quot;sticking&quot;"
date: 2007-09-13
forum: Desktop Environments
---

### Post by jeepfreak2002 on 2007-09-13
Well, my honey just bought me a 22" wide screen, 2ms refresh LCD monitor, and I'm in love... with her too... as far as this monitor goes, I'm struggling to get the max resolution to "stick"  It's 1680x1050, but I have to reset the resolution after every reboot.

I think that there is something going on with the Envy nVidia driver not being allowed to "save to the X configuration file" I get:

Unable to remove old X config backup file

It's no big deal - As long as I'm playing Guild Wars, I'm happy, but it is a bit of a pain.  Any Ideas????

---

### Post by PurposeOfReason on 2007-09-13
Post your xorg.conf file and what drivers your using. What card model?

---

### Post by Pancetilla on 2007-09-14
Hi

Your favourite resolution (1680x1050)  must be in first place in xorg.conf (in modes section).

Edit manually your xorg, avoid xorgconfig and the likes (it's not difficult and you'll do it faster and learn a lot) and don't forget to backup it first and then edit it as root (sudo gedit /etc/X11/xorg.conf)

---

### Post by PmDematagoda on 2007-09-14
You can do the necessary changes by loading nvidia settings using 

```
sudo nvidia-settings
```

which loads the nvidia-settings manager in root mode which allows you to change the xorg.conf file.

---

### Post by wkulecz on 2007-09-14
sudo nvidia-settings didn't work for me.  Don't know why, but sudo -i and then running nvidia-settings did.  So try both if the other doesn't work.

--wally.

---

### Post by jeepfreak2002 on 2007-09-15
Let me give you a little more background info:

I am running an nVidia Geforce 7600GT

I have the nVidia driver installed through Envy.  Everything seems ducky, except when the computer runs an update, and then all of the x- info gets screwed and I have the rebuild the x- package (I think that is correct)

If I go into the "nVidia settings" that are available because of Envy, I can adjust every setting under the sun, but it will not allow me to "save to x configuration file"  I don't know if I have to be root, or what, but I would expect it to prompt me for a password it that is what is needed.

#2:  Are you saying just open a terminal and type: sudo nvidia-settings???
What exactly does that do?

---

### Post by sonoro on 2007-09-18
Thanks! This worked for me. I used Envy and was having the same problem. Sudo runs commands with root priveleges. So when the settings menu pops up after you run it, change your settings, and then save your x configuration file.
=)

---


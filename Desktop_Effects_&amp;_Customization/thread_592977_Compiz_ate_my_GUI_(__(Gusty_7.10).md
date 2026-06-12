---
title: "Compiz ate my GUI :(  (Gusty 7.10)"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by Nexusx6 on 2007-10-26
Hey all,

This morning I got Gusty up and running, installed everything including drivers for my Nvida 8800GTX and all seemed to be okay. I wanted to get compiz going, and I read that CompizFusion comes by default with Gusty, so I installed the Settings Manager via Adept and ran it -- except none of the special effects loaded. Plenty of things had check boxes next to them but there was still nothing to be seen.

Attempting to figure why I wasn't getting any wiggles or shakes or any of the other cool things CompizFusion does, I check other fourms, find a poster telling someone else to "Type compiz into the terminal and tell us what happens"

Out of curiosity, I did the samething. No sooner than when I hit enter my screen turns black, then Adept goes full screen and the taskbar is gone completely. I hit Alt+Ctrl+BKSPC and restart. I'm prompted with a text logon screen, so I login and type *startx*

The read out looks like this:
> 
(EE) Failed to load module 'nvidia' (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
XI0: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

It looks like compiz decimated my video drivers some how :sad:
Is there anyway to fix this without doing a full re-install? I'd try to re-install the drivers via apt-get, but I'm still new to linux and I don't know how I'd go about doing that. I sincerely appreciate any help.

UPDATE:
I tried doing a driver re-install by doing 
> sudo apt-get remove linux-restricted-modules-generic
followed by:
> sudo apt-get install linux-restricted-modules-generic
Still no dice. Same exact message

---

### Post by kelbizzle on 2007-10-26
Did you make a backup of your xorg.conf file located in /etc/X11/ folder?
Type:
```
ls /etc/X11
```

See if you have a back up to copy and replace your current xorg.conf like for me it would be 

```
cp /etc/X11/xorg.conf.bak xorg.conf
```

then restart gdm 
```
sudo /etc/init.d/gdm restart
```

---

### Post by Nexusx6 on 2007-10-26
> Did you make a backup of your xorg.conf file located in /etc/X11/ folder?

No :( And it doesn't look like there were any automatic backup's ethier.

---

### Post by kelbizzle on 2007-10-26
Well you should be able to reconfigure the xserver until then.
```
sudo dpkg-reconfigure xserver-xorg
```

---


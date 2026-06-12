---
title: "screen resolution set to native for display but cut off"
date: 2009-03-06
forum: Desktop Environments
---

### Post by treejet on 2009-03-06
screen resolution set to native for display but cut off to point where toolbars are not accessible. The display that I am using is a Sony Bravia 40 inch HDTV. Graphics card MSI OC 9800 GTX+, ubuntu 8.10  Just installed from windows Vista(caught a phising virus from a download that my anti-virus didnt pick up) and had the same problem and and had to use the nvidia control panel to adjust screen to fit my display. Does anyone know where i can do this???

---

### Post by treejet on 2009-03-06
treejet@treejet-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.

treejet@treejet-desktop:~$ 

I did this after i found the Nvidia x server settings and it told me that i was not using the Nvidia X driver

---

### Post by treejet on 2009-03-06
update: by switching inputs from HDMI to PC on my TV I see everything in the native resolution, but graphical quality is not what i paid good money to do. any ideas?

---

### Post by Godly on 2009-03-27
I'm experiencing the same issue on my LG 42 inch LCD. I was hoping someone had posted a reply so I can attempt a resolution. Nothing yet.:(

---

### Post by bigbencg on 2009-03-27
If I understand correctly when using the HDMI port, you screen is shifted outside of the viewing boundaries of the TV correct?

I have dealth with this issue myself, the problem lies in the Hsync, Vsync, and refresh rate of the TV.

Can you reconnect the HDMI and post the output of 
```
xrandr -q
```

---

### Post by stillgreener on 2009-03-28
i'm also having the same problem and just posted my xandr settings and in the end I figured that I did not have the television set to native resolution (which corrected the problem).  (couldn't delete this post but hopefully it will help someone else who also did not read the thread title)

---


---
title: "Gutsy - Gnome broken after update"
date: 2008-02-11
forum: Desktop Environments
---

### Post by munza on 2008-02-11
Ubuntu Gutsy 7.10 with all recent security updates.

After updating this morning, nothing major just these two:
[UPGRADE] firefox 2.0.0.11+2nobinonly-0ubuntu0.7.10 -> 2.0.0.12+2nobinonly+2-0ubuntu0.7.10
[UPGRADE] firefox-gnome-support 2.0.0.11+2nobinonly-0ubuntu0.7.10 -> 2.0.0.12+2nobinonly+2-0ubuntu0.7.10

All my users can no longer login to Gnome (KDE works ok)
They all get:
The panel has encountered a fatal error
The panel could not register with the bonobo-activation server (error code:3) and will exit.
It may be automatically restarted.

Followed by a blank desktop, no panel and no repsonse to mouse clicks.

---

### Post by NilsHG on 2008-02-12
similar problem here. 
the updatesinstalled and everything did work.

i then fooled around with compiz ccsm. in general options i set desktops to "2" and i when i clicked the panel icon to go to the second desktop i got a totally blank screen with mycustom  wallpaper and the mouse cursor. i cannot go back to the first desktop. 
i restarted X with ctrl+alt+backspace and now when i log back in i get the brown background and nothing else, no panels etc.

help please :)

---

### Post by NilsHG on 2008-02-12
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this messed up my xorg.conf at first. from the console i stopped gdm, manually edited xorg.conf with vi and set it to the right driver. restared gdm and i am back on my normal desktop... not sure what caused the problem but everything works for me now. 
cheers

---

### Post by graphius on 2008-02-15
I am having the same problem. I started a [thread]("http://ubuntuforums.org/showthread.php?t=695919&highlight=desktops") myself.
I tried to reconfigure as per NilsHG, but no difference. I still can't switch desktops...

---

### Post by graphius on 2008-02-15
I GOT IT !!!
under compiz settings (Advanced Desktop settings) go to general options, then set the number of virtual desktops to 1. You can set the vertical and horizontal size to whatever you require.

I really love Linux when it works...

---

### Post by xlv1000 on 2008-02-17
same with me.No left,no right click,no panels I just can run some programes from a list when i press alt+F2:(

---

### Post by graphius on 2008-02-17
With the help of another thread I found out it is a compiz issue...
under compiz settings (Advanced Desktop settings) go to general options, then set the number of virtual desktops to 1. You can set the vertical and horizontal size to whatever you require.
It is a bit counter-intuitive, and I am not sure which update caused the problem, but my system is working fine now...

---


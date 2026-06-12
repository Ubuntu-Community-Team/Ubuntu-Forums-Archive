---
title: "n00b installed ubuntu-desktop and..."
date: 2009-02-16
forum: Desktop Environments
---

### Post by cozee on 2009-02-16
I installed it from a tutorial with this command line to start it " /etc/init.d/gdm start"
Putty says " Starting GNOME Display Manager...[ OK ]"

But wheres my display nothing pops up etc.I chose a server that has ubuntu 8.04 server on they didnt have the option for desktop and I really need one.
I have webmin installed correctly.Im fairly new to linux but im getting there slowly but ive always had a GUI to fall back onto.
Thanks for any help as google doesnt help n00bs...:)
..cozee

---

### Post by Perryg on 2009-02-16
> **cozee said:**
> I installed it from a tutorial with this command line to start it " /etc/init.d/gdm start"
Putty says " Starting GNOME Display Manager...[ OK ]"

But wheres my display nothing pops up etc.I chose a server that has ubuntu 8.04 server on they didnt have the option for desktop and I really need one.
I have webmin installed correctly.Im fairly new to linux but im getting there slowly but ive always had a GUI to fall back onto.
Thanks for any help as google doesnt help n00bs...:)
..cozee

Your entry is a little confusing, but if I understand you have Ubuntu 8.04 and have installed gdm.  If that is the case you can (from terminal) type startx and it should load you up.

---

### Post by ugm6hr on 2009-02-16
Try adding this lot:

```
sudo apt-get install xorg gdm acpi-support gnome-session gnome-menus gnome-panel gnome-applets gnome-volume-manager gnome-power-manager metacity nautilus gnome-screensaver xscreensaver menu gnome-utils gnome-system-tools libgnomevfs2-extra smbfs
```

You have to be online with a wired internet connection.

---

### Post by cozee on 2009-02-17
Im on a server thats rented.
It didnt have a desktop option although ive just sent a ticket requesting at least a gui version.
I only need it for websurfing and using either transmission or deluge.Its got 2x150gb HDD in so i wanna be able to see that also.
Im new to linux but am slowly learning webmin is installed and working.
Thanks in advance.....cozee

[color=red]**EdiT**[/color]
I tried that command ugm6hr but get the same results.I use the "startx" command it says that its already running and to run a command that doesnt make a difference.I try the "/etc/init.d/gdm start" and it says " Starting GNOME Display Manager...[ OK ]" but still no display:(

---

### Post by Perryg on 2009-02-17
> **cozee said:**
> Im on a server thats rented.
It didnt have a desktop option although ive just sent a ticket requesting at least a gui version.
I only need it for websurfing and using either transmission or deluge.Its got 2x150gb HDD in so i wanna be able to see that also.
Im new to linux but am slowly learning webmin is installed and working.
Thanks in advance.....cozee

[color=red]**EdiT**[/color]
I tried that command ugm6hr but get the same results.I use the "startx" command it says that its already running and to run a command that doesnt make a difference.I try the "/etc/init.d/gdm start" and it says " Starting GNOME Display Manager...[ OK ]" but still no display:(


If all of these are loaded and you are still in a terminal window try <ctrl>-<alt>-F7 and see if it takes you back to the GUI.

---


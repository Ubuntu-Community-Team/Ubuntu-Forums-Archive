---
title: "noob problem"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Hopelessness on 2006-06-20
i have installed ubuntu twice now, but when i boot it up it goes to the command line. how do i load gnome? its getting annoying now ](*,) 
thanks

---

### Post by Ramses de Norre on 2006-06-20
What output do you get when you log in and execute ```
sudo /etc/init.d/gdm start
```

---

### Post by givré on 2006-06-20
Which install cd didi you choose, the desktop, the server or the alternate one?
Try to start gnome with
```
sudo /etc/init.d/gdm start
```

---

### Post by Hopelessness on 2006-06-20
when i execute ```
sudo /etc/init.d/gdm start
``` it asks for a password then shows ```
sudo: /etc/init.d/gdm: command not found
```
the same shows with the second suggestion
and i am pretty sure it was the desktop version [i got it from a pc answers dvd]

---

### Post by tommcd on 2006-06-20
If that does not work you may need to reconfigure Xorg. At the command prompt type:
sudo dpkg-reconfigure xserver-xorg

you will have to answer questions about you keyboard, mouse and monitor (you can likely go with defaults to all). At the end choose 'medium' for monitor configuration. Choose monitor resolutions by selecting them with the space bar. At the end type: 'sudo reboot' (without quotes). You should now have the GUI login screen.
If this still doesn't work, reconfigure Xorg again, but choose 'vesa' or 'vga' for monitor driver. Hope this helps.

---

### Post by Hopelessness on 2006-06-20
it says:
```
Package 'xserver-xorg' is not installed and no info is available.
```
then there is a load of usage info but no configuration menu!

---

### Post by givré on 2006-06-20
Be sure that it was the dsktop cd is quite simple, if you install it via a live cd and a graphical installer, it was the desktop cd.
If it wasn't reinstall via an alternate or a dektop cd (alternate recommended)
if it was, you are not the first personn to have this problem (the desktop cd is quite buggy).
If you have internet access, try that
```
wget -c http://www.psychocats.net/ubuntu/sources.list
sudo chown root:root sources.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list_empty
sudo cp sources.list /etc/apt/sources.list
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```
If not, reinstall via an alternate cd

---

### Post by tommcd on 2006-06-20
You could try (if above post don't work or no internet access):
sudo dpkg-reconfigure -phigh xserver-xorg
I think this creates the xorg file from scatch if none is found.

---

### Post by Kouya on 2006-06-20
it sounds like you used the server cd to install. switch to the desktop one. I made such a mistake during my first time installing ubuntu.

---


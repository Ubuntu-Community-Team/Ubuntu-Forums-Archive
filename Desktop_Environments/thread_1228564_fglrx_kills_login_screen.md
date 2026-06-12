---
title: "fglrx kills login screen?"
date: 2009-08-01
forum: Desktop Environments
---

### Post by Kreuger on 2009-08-01
I had a problem with my display exactly like [this]("https://bugs.launchpad.net/ubuntu/+bug/368877") so I tried installing envy and used it to install fglrx as the driver. Now when I reboot, I get all kinds of weird colours on the screen (it looks broken) and it's unusable. There's no gdm or anything. I tried using CTRL ALT F1 to get a terminal and it didnt work. I basically pressed every key and nothing happened. During the boot process before it tries to load gdm there's a chance to type in the terminal. I can type my username and part of my password then it tries to load the gdm and Im SOL. I want to get rid of fglrx because I have found some alternatives to try and now I cant.

Edit: I was able to boot into recovery mode and I replaced the xorg.conf with my backed up version and it gave me a black screen so I regenerated it and now I just get a black screen still.

---

### Post by bagy on 2009-10-04
sudo apt-get remove xorg-driver-fglrx

if you install from .run file, start in recovery mode. in conzole type 
```
cd /usr/share/ati
```
then type ```
ls
```
and find fglrx-uninstall
```
./fglrx-uninstall
```
and reboot...

---


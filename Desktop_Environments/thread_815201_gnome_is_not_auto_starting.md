---
title: "gnome is not auto starting"
date: 2008-06-01
forum: Desktop Environments
---

### Post by honeydew on 2008-06-01
hello.. what is the function that causes gdm to auto start on the live cd?  like you stick the liveCD in.. and it automagikly shifts to window manager.  I am using KVM to create my custom liveCD however its not automaticly shifting to the gnome session like the default live cd does.  It just pops up with a shell session.  Any ideas... sorry for scatered post I dont really know what Im asking for.

cheers!

---

### Post by NikoC on 2008-06-01
from command line it's:
sudo /etc/init.d/gdm start

---

### Post by honeydew on 2008-06-01
nah.. I figured it out.. I had xserver-xorg installed but needed xorg installed..

thanks for your help!

---


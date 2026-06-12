---
title: "I broke my xorg.conf"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Trashbear on 2006-06-21
I didnt go all the way through with an nvidia driver install tutorial or something.
Then rm'd the xorg.conf out of anger. Is there anything I can do to fix it?
Like a basic xorg.conf I can use just to get into x and sort things out?

---

### Post by Ramses de Norre on 2006-06-21
ctrl-alt-F1 to get to a terminal, log in and do
```
sudo dpkg-reconfigure xserver-xorg
```
Follow all the steps and then do ```
sudo /etc/init.d/gdm start
``` to go to your login screen (replace gdm by kdm when you're on kubuntu).

---

### Post by tseliot on 2006-06-21
Try with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Trashbear on 2006-06-21
Thanks for the quick replies, Ill try this and see what happens.

---

### Post by Trashbear on 2006-06-21
So I'm back in Gnome with everything fine but it seems I have no 3d acceleration even after installing the nvidia glx packages and dependencies through Synaptic package manager.

---

### Post by tseliot on 2006-06-21
[QUOTE=Trashbear]So I'm back in Gnome with everything fine but it seems I have no 3d acceleration even after installing the nvidia glx packages and dependencies through Synaptic package manager.[/QUOTE]
Try method 1 of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by Trashbear on 2006-06-21
[QUOTE=tseliot]Try method 1 of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")[/QUOTE]

Awesome, everything is working fine again. Thanks alot!:D

---


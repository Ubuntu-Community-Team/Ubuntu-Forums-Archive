---
title: "xorg.config"
date: 2005-10-14
forum: Desktop Environments
---

### Post by greengrass on 2005-10-14
How do you edit this file?

I tried typing gksudo  and sudo nano  but it still comes up   read only

---

### Post by Karasu Tengu on 2005-10-14
[QUOTE=greengrass]How do you edit this file?
I tried typing gksudo  and sudo nano  but it still comes up   read only[/QUOTE]

sudo /etc/X11/xorg.conf

if its in read only... are you using a liveCD??

---

### Post by greengrass on 2005-10-14
this is a full install   trying to get the mouse to work

---

### Post by wezzer-foo on 2005-10-14
You can also get your mouse to work by running command
sudo dpkg-reconfigure xserver-xorg

---

### Post by daschl on 2005-10-14
```

sudo gedit /etc/X11/xorg.conf

```

but before i recommend this:

```

$ cd /etc/X11/
$ sudo cp xorg.conf xorg.conf.backup

```

good luck :)

---

### Post by xyzzyman on 2005-10-14
With nano you have to do a 'nano -w' to let you write the file. So the command to be is:

```
sudo nano -w /etc/X11/xorg.conf
```

or if you like a gui use:

```
sudo gedit /etc/X11/xorg.conf
```

---


---
title: "theme gone weird after x crash"
date: 2010-05-01
forum: Desktop Environments
---

### Post by mshenrick on 2010-05-01
hey! i just upgraded to lucid, and x has been very unstable. after one crash were it would not restart i typed

```
startx
```then the theme which used to look like this (not my pic)

[ATTACH]155000[/ATTACH]
:P

went to this (ignore the wallpaper)

[ATTACH]155001[/ATTACH]
:(:confused:

though compiz still works. changing the theme does barely anything.

can anyone help!?

---

### Post by The Fiddler on 2010-05-01
I've seen this happen before (on Karmic, too).

Restarting X usually fixes the error. If it doesn't, try rebooting and/or checking the disk for errors.

---

### Post by mhgsys on 2010-05-01
rather type 
```
sudo service gdm start
```
or 
```
sudo /etc/init.d/gdm start
```

instead of startx



In your case I'm pretty sure rebooting solves your problem.
But if you don't want to reboot try opening up a terminal and typ

```
sudo service gdm restart
```

---

### Post by mshenrick on 2010-05-01
thanks for the help but rebooting has just made it worse. it now only works in so-low-its-unbeliveable-and-unusable-graphics mode

---

### Post by mhgsys on 2010-05-01
no problem  

Switch to tty by pressing ```
ctrl + alt +f1
```

login with your username and password
typ:

```
sudo /etc/init.d/gdm stop
```

followed by your password

then type
```
sudo Xorg -configure
```

and move the generated xorg.conf.new to /etc/X11/xorg.conf
with:
```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

edit the /etc/X11/xorg.conf with 
```
sudo nano /etc/X11/xorg.conf
```
and change the **driver in section Device **to** vesa**

then restart gdm with 
```
sudo /etc/init.d/gdm start
```

You'll be working in vesa mode again; which will give you a little bit  better mode then a so-low-its-unbeliveable-and-unusable-graphics mode.

Still; once in vesa mode; try reinstalling the proper graphics drivers.

---


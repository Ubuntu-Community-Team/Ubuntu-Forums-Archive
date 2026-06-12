---
title: "xorg.conf editing..."
date: 2006-05-15
forum: Desktop Environments
---

### Post by i++ on 2006-05-15
Hi all :) 

im a total newbie at this, but im hoping to learn! however, learning is a bit harder without a GUI... i recently installed Ubuntu 5.10 onto my Desktop PC, but X fails to load. I think its because my gfx card (Radeon X800 GTO) has the driver set at ati, and it should be radeon. i try to edit the file /etc/X11/xorg.conf but it wont let me save the changes (i used vi) i have given myself all permissions etc... any idea's how i can do this?

thanks in advance!

a.new.bee

---

### Post by bluevoodoo1 on 2006-05-15
did you use 'sudo' ??

```
sudo vi /etc/X11/xorg.conf
```

I usually use nano instead of vi, (with nano... to save it's ctrl+o, to exit ctrl+x)

you can also do it graphically!

```
sudo dpkg-reconfigure xserver-xorg
```

then restart X with ctrl+alt+backspace. If you get dumped at the command line, run ```
sudo /etc/init.d/gdm restart
``` to get back to the graphical login.

---

### Post by aysiu on 2006-05-15
[QUOTE=bluevoodoo1]
I usually use nano instead of vi, (with nano... to save it's ctrl+o, to exit ctrl+x)[/QUOTE] So do I: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

---

### Post by i++ on 2006-05-15
thanks a million! i will go try this asap :)


amazing! worked first time, thanks so much to you both!

i++

---

### Post by robglinka on 2006-05-15
Hey, Rule #1, always back up config files before you edit them!!! Espeically when working with the xorg.conf file, I bet you, and just about everyone else will screw it up once or twice before you get it running. You always want to have a working backup.

If you get something partially working, back that up too.

---


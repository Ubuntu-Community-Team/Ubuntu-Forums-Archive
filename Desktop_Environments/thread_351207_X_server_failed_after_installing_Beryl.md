---
title: "X server failed after installing Beryl"
date: 2007-02-01
forum: Desktop Environments
---

### Post by spacegypsy on 2007-02-01
Helo,

I'v been  trying to install Beryl following [this guide]("https://wiki.ubuntu.com/NederlandstaligeDocumentatie/Beryl?highlight=%28beryl%29") and it worked partially.
But when I rebooted my machine I got the message ;
> Failed to start X server (your graphical interface). It's likely that it is not set up correctly. Would you like to vieuw the X server output to diagnose the problem?

I safed my previous xorg.conf on an usb-stick and want to reinstall this one.

Does someone know how I can do this and if it will resolve my problem?

I've been trying to copy my good xorg.conf with;
sudo cp /media/usbdisk/location/of/file /destination/of/file
but it didn't work

thanx

---

### Post by glabouni on 2007-02-01
hmm. 
what is the error you get from the cp command ?

only reason I can think of right now is your location/of/file is wrong or unaccessible.

as an advice, you should have a backup copy of your important conf file avaialble in the same directory the conf file reside. for example /etc/X11/xorg.conf.backupcopy

---

### Post by spacegypsy on 2007-02-01
I got the message;

> cp cannot stat '/media/usbdisk/xorg.conf' : No such file or directory

I also tried; ```
sudo cp /usbdisk/xorg.conf /etc/X11/xorg.conf
```

with te same result

---

### Post by spacegypsy on 2007-02-01
Must be also a way to edit xorg.conf without graphical interface.

I tried; ```
sudo gedit /etc/X11/xorg.conf
```

but got the message, > connot open display: (null)

---

### Post by glabouni on 2007-02-01
as i thought, the file is not available. 
seems to me your usb drive is not mounted, hence its content is not available.

you should try to mount it manually.

what is the output of 
```
sudo fdisk -l
```

it is possible to edit xorg.conf from terminal.
gedit is intended to work under gnome, to edit xorg.conf you'll need a terminal text editor. 
you can try using nano instead of gedit.

-edit-
my bad I mistyped the command. now fixed.

---

### Post by spacegypsy on 2007-02-01
output sudo fidisk -l ;

> sudo: fidsk: command not found

tried also mcedit but here also command not found

I'll try nano

---

### Post by spacegypsy on 2007-02-01
Problem solved! :D 

with nano I re-edited my xorg.conf file like it was


thanx glabouni for your help and advice :guitar:

---

### Post by glabouni on 2007-02-01
you're welcome

---


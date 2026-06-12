---
title: "USB pen drive udev rules and autofs automounting."
date: 2008-11-17
forum: Desktop Environments
---

### Post by lvgandhi on 2008-11-17
I have following rules file in /etc/udev/rules.d/
lvgandhi@lvghomepc:~$ cat /etc/udev/rules.d/010_local.rules
BUS=="scsi", SYSFS{model}=="External Drive", KERNEL=="sd?1", NAME="%k", SYMLINK="ehd"
BUS=="usb", SYSFS{model}=="Cruzer Micro", KERNEL=="sd?1", NAME="%k", SYMLINK="flash", MODE="0775"
and I have /etc/auto.master as below
/var/autofs/removable   /etc/auto.removable     --timeout=2
and auto.removable as below
flash   -fstype=vfat,rw,uid=1000,umask=022,posix,shortname=winnt       :/dev/flash
ehd     -fstype=vfat,rw,uid=1000,umask=022,posix,shortname=winnt         :/dev/ehd

My first problem is that udev rules doesn't make /dev/flash. Because of that I am unable to see further. I changed udev rules line as 
SUBSYSTEMS=="usb",  DRIVERS=="usb",  ATTRS{product}=="Cruzer Micro", NAME="%k", SYMLINK="flash", MODE="0775"
This also doesn't make /dev/flash.
How to go about it?

---

### Post by prshah on 2008-11-17
> **lvgandhi said:**
> 
How to go ablout it?

Is there any reason why you can't just put an "autorun.sh" file in the root of the USB device? That will be autorun.

Of course this is not viable if you want an autorun on _every) USB device plugged in.

---

### Post by lvgandhi on 2008-11-17
Actually I want to to sync with unison. With these local rule file for udev and auto.removable for autofs, things work in Debian Etch. Here in kubuntu 8.04 even device /dev/flash is not formed with the udev local-rules file. Hence I would like to know how udev is handled in kubuntu?

---

### Post by lvgandhi on 2008-11-18
Now I could get made /dev/flash by tweaking udev rules as explained in some other thread. But still I am unable to automount using autofs my usb stick. I think some other configuration is is not allowing/redirecting. How to do auitomounting using autofs in kubuntu? details of autofs configuraion is in my first post.

---


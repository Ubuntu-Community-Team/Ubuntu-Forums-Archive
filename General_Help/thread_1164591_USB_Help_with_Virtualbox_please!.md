---
title: "USB Help with Virtualbox please!"
date: 2009-05-19
forum: General Help
---

### Post by DAE_JA_VOO on 2009-05-19
Hi there everyone. 

I just got an iPod Shuffle (3G), and I'd love to be able to do all my synchronizing in XP in a virtual PC, instead of having to boot into XP every time. So here's the problem. I cannot connect my shuffle in the virtual machine. In fact, I can't connect ANY USB devices. The menu is greyed out completely, like this:

[img]http://img32.imageshack.us/img32/4347/screenshot003z.jpg[/img]

I'm using Jaunty.

Any suggestions? (and no, I don't want to use anything except iTunes. NOTHING seems to support my Shuffle)

Thanks!

---

### Post by raptor2552 on 2009-05-19
I don't know why this isn't setup automatically but you'll need to edit some files. Remember to make backup copies of the files shown below before editing.

Step one open a terminal and enter:
```
gksu gedit /etc/init.d/mountdevsubfs.sh
```

find the section that looks like:
```
	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts-onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
```

open a new line directly after the above and before the } (curly brace) and add:
```
	#
	# Magic to make /proc/bus/usb work
	# following four lines need to be uncommented for use with VirtualBox
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

save and close.

Step two enter in a terminal:
```
grep vbox /etc/group
```

you should see a line like:
```
vboxusers:x:[COLOR="Red"]124[/COLOR]:mike
```

take note of the group id (marked in red)

Step three enter in a terminal:
```
gksu gedit /etc/fstab
```

scroll to the end and add:
```
# mount usb ports for VirtualBox
none /proc/bus/usb usbfs [COLOR="Red"]devgid=124[/COLOR],devmode=664 0 0
```
being sure to substitute the group id found in your /etc/group file and use it in the above line where it says [COLOR="Red"]devgid=124[/COLOR]

save and close, reboot to pick up the changes. You should now be able to use USB ports in Virtualbox.

Good luck

---

### Post by DAE_JA_VOO on 2009-05-20
Thanks for your post!

I did all of that, saved it, etc, still no joy. Everything is still greyed out :(

---

### Post by kpkeerthi on 2009-05-20
[http://ubuntuforums.org/showpost.php?p=7307255&postcount=4]("http://ubuntuforums.org/showpost.php?p=7307255&postcount=4")

Its based on the instructions from the virtualbox manual and it worked for me. [http://www.virtualbox.org/manual/UserManual.html#id2661849]("http://www.virtualbox.org/manual/UserManual.html#id2661849")

---

### Post by mixmaster on 2009-05-20
From memory the open source edition of virtualbox (ie the one in the repositories) does not support usb.  You can get usb from the PUE (personal use and evaluation) binary edition offered by Sun.

Differences are listed here : [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by raptor2552 on 2009-05-20
I suppose you have in Settings enabled USB 2.0 support and have loaded the Guest Additions.

---

### Post by DAE_JA_VOO on 2009-05-24
Thanks guy! After installing the closed source version, and doing this:

> **kpkeerthi said:**
> [http://ubuntuforums.org/showpost.php?p=7307255&postcount=4]("http://ubuntuforums.org/showpost.php?p=7307255&postcount=4")

Its based on the instructions from the virtualbox manual and it worked for me. [http://www.virtualbox.org/manual/UserManual.html#id2661849]("http://www.virtualbox.org/manual/UserManual.html#id2661849")

I came right. Thanks :)

---


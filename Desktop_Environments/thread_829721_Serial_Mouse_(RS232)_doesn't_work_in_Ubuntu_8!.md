---
title: "Serial Mouse (RS232) doesn't work in Ubuntu 8!"
date: 2008-06-15
forum: Desktop Environments
---

### Post by akap475a on 2008-06-15
Just like in Ubuntu 7 the serial mouse doesn't work in Ubuntu 8!

In the previous Ubuntu version (7) i had already fixed that by editing to /etc/X11/xorg.conf according to this info --> [http://ubuntuforums.org/showthread.php?t=385646](http://ubuntuforums.org/showthread.php?t=385646)  However this file (xorg.conf) has not the same format to edit it accordingly... :(

---

### Post by akap475a on 2008-06-15
I found solution to my problem!

Edit /etc/X11/xorg.conf
...
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
        Option          "CorePointer"
	Option		"Device"	"/etc/X11/mouse"
	Option		"Protocol"	"microsoft"
...
-----------------------------------------------------------------------

After editing the above file just press the following command with Super User privilleges

ln -sf /dev/ttyS0 /etc/X11/mouse

---


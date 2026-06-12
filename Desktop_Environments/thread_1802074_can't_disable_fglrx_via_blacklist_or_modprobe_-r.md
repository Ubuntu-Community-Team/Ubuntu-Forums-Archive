---
title: "can't disable fglrx via blacklist or modprobe -r"
date: 2011-07-11
forum: Desktop Environments
---

### Post by Yehonal on 2011-07-11
hi guys!

i'm using different videocard with the same installation of ubuntu, the first one is an integrated card ..the second one is a radeon gpu.. and now i need to disable fglrx when i'm with integrated card ( i've different issues when fglrx is running with standard vga)
so i've created a script that try to disable/enable fglrx at boot , it starts at runlevel before x server using this way: [http://ubuntuforums.org/showthread.php?t=1287967](http://ubuntuforums.org/showthread.php?t=1287967)

but my script is this instead:

```

#!/bin/sh

/etc/init.d/gdm stop

if grep -q disablefglrx /proc/cmdline
then
        mv -f /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
	sed -i '/blacklist fglrx/ d' /etc/modprobe.d/blacklist.conf
	echo "blacklist fglrx" >> /etc/modprobe.d/blacklist.conf
	modprobe -r fglrx
elif grep -q enablefglrx /proc/cmdline 
then
       	mv -f /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
	sed -i '/blacklist fglrx/ d' /etc/modprobe.d/blacklist.conf
	modprobe fglrx
fi

sudo depmod -a
/etc/init.d/gdm start

```

as you can see there's also some code that could be useless, but i've included it to make sure to use all methods i know.

However, nothing happen, fglrx always starts with gdm .

can anyone explain me where is the problem? thanks


P.S. i didn't paste grub.conf because the conditions in the script work aswell since i can see xorg.conf and blacklist modifications at each selected menuentry

---

### Post by Yehonal on 2011-07-12
bump

please let me know how to disable fglrx

---

### Post by Bucky Ball on 2011-07-12
Uninstall it. System>Administration>Synaptic Package Manager. Search for it and remove.

---

### Post by Yehonal on 2011-07-12
> **Bucky Ball said:**
> Uninstall it. System>Administration>Synaptic Package Manager. Search for it and remove.

please read the post before, i need to disable and enable periodically..

so i want to know if it's possible .. 

install and uninstall is not the proper way for me.

---

### Post by Yehonal on 2011-07-12
anyone can help me?

i tried also using "update-initramfs -u" after module blacklisted, but nothing..

now i'm thinking to try renaming /etc/alternatives/xorg_extra_modules/modules ( dir of fglrx ) 

but i don't think it's the best way

---


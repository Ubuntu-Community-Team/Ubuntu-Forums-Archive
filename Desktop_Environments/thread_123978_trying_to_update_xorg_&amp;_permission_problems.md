---
title: "trying to update xorg &amp; permission problems"
date: 2006-01-31
forum: Desktop Environments
---

### Post by bud986 on 2006-01-31
Hey

Iam a "happy" owner of an n610c ^^ but the thing is that im having some, problems to update my xorg 6.8 to 6.9 in order to get my ati mobility radeon 7500 working. 
:-k 

It seems that im having some enoying permissioin problems. Im not able to move my or delete my current xorg (usr/x11r6/bin)

and occording to this:
[http://dri.freedesktop.org/wiki/Download#head-ecc2e81644411c145ce0e78cbb89b8a6daaf2f40](http://dri.freedesktop.org/wiki/Download#head-ecc2e81644411c145ce0e78cbb89b8a6daaf2f40)



    *

      Download Xorg.bz2 and modules.tar.bz2.
    *

      Make a backup of /usr/X11R6/lib/modules and usr/X11R6/bin/Xorg (if present) and move them out of the way.
    *

      Uncompress Xorg.bz2, copy it to /usr/X11R6/bin and set permissions.
    *

      Uncompress Xorg-modules.tar.bz2 in /usr/X11R6/lib.
    *

      Make a symbolic link from /etc/X11/X to /usr/X11R6/bin/Xorg if it's not there yet or points somewhere else.
    *

      If needed copy XF86Config-4 to xorg.conf and change the keyboard driver from "keyboard" to "kbd".


> 
wget [http://dri.freedesktop.org/snapshots/extras/Xorg.bz2](http://dri.freedesktop.org/snapshots/extras/Xorg.bz2)
wget [http://dri.freedesktop.org/snapshots/extras/modules.tar.bz2](http://dri.freedesktop.org/snapshots/extras/modules.tar.bz2)
 
mv -f /usr/X11R6/bin/Xorg /usr/X11R6/bin/Xorg.backup
bzip2 -d Xorg.bz2
cp Xorg /usr/X11R6/bin
chmod 4755 /usr/X11R6/bin/Xorg
 
mv /usr/X11R6/lib/modules /usr/X11R6/lib/modules.backup
tar -C /usr/X11R6/lib -xjf modules.tar.bz2
 
cd /etc/X11
rm X
ln -s /usr/X11R6/bin/Xorg X
if [ -f XF86Config-4 ]; then cp XF86Config-4 xorg.conf; fi
<edit xorg.conf>


//Have a nice day :)

---

### Post by aysiu on 2006-01-31
Try either Alt-F2 ```
gksudo nautilus
``` or Applications > Accessories > Terminal ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by bud986 on 2006-01-31
The file om trying replace is > /usr/X11R6/bin/Xorg with a newer one :o 

In the reply: > sudo gedit /etc/X11/xorg.conf 
I do belive that I that aims for the .config 

//Thank you fo your time:D

---


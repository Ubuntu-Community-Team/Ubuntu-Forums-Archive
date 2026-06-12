---
title: "root-tail"
date: 2005-05-04
forum: Desktop Environments
---

### Post by flightcrank on 2005-05-04
hi, i want to install a program called root-tail, basicly it shows you for examplw whats happining in var/log/syslog in real time as it happes on your desktop! looks nice so i decieded id try and install it,

so i typed

```
sudo apt-get install root-tail
```

that did the trick. how ever i load it from console and i cant see anything, after searching on the net i heard  gnome draws the desktop over it, has any one fgred out a way to get this to work under ubuntu ?

---

### Post by Professor X on 2005-05-04
The only fix I know of is to use the Gconf editor and go to apps -> nautilius -> preferences.  Uncheck the box for 'Show Desktop'.  Root-tail will work, but you will lose all icons and commands on your desktop.  Not worth it me thinks.

---

### Post by flightcrank on 2005-05-05
[QUOTE=Professor X]The only fix I know of is to use the Gconf editor and go to apps -> nautilius -> preferences.  Uncheck the box for 'Show Desktop'.  Root-tail will work, but you will lose all icons and commands on your desktop.  Not worth it me thinks.[/QUOTE]
 there must be some other way !

---

### Post by flightcrank on 2005-05-05
i found this program

[http://root-portal.sourceforge.net/](http://root-portal.sourceforge.net/)

seems to do the same thing, but works for gnome :D

---

### Post by hal8000 on 2005-06-05
Good hunting! I downloaded version 0.52 of root-portal,  but am missing some X11
headers. What version did you install or which X11 libraries do I need to install
? 

configure: error: You need to have the X11 libraries and headers installed
./configure: line 20605: exit: or: numeric argument required
./configure: line 20605: exit: or: numeric argument required

---

### Post by angkor on 2005-06-06
What about:

sudo apt-get install root-portal

 :smile:

---

### Post by jonspinks on 2005-07-31
I've been trying to get this going in XFCE but a similar approach should work with Gnome.  You basically need to provide the XID of the root window to use before it will work.  

After looking around on a few different sites this script should get you going:

#!/bin/sh
WIDTH=`xwininfo -root | grep Width | cut -d":" -f2`
WIDTH=`expr $WIDTH - 20`
WIDTH=${WIDTH}"x150-10-50"
root-tail -g $WIDTH -id `xprop -root XFCE_DESKTOP_WINDOW | cut -d' ' -f5` /dev/xconsole,green /var/log/messages,red


However if something similar doesn't work for Gnome users then someone has hacked root-tail to work with Nautilus here:

[http://www.tobert.org/unix/](http://www.tobert.org/unix/)


Jon

---


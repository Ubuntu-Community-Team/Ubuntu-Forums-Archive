---
title: "Printing Problem"
date: 2005-12-04
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2005-12-04
My printer, a "hp deskjet 3420" is connected to my ubuntu computer by usb. I cannot open the "gnome-cups-manager" and alas, cannot print. I need to get this working soon for school. I cannot contact [http://localhost:631](http://localhost:631)
When i try to open the printing manager from terminal, I get this error
```
root@ubuntu:~# gnome-cups-manager

** (gnome-cups-manager:9646): WARNING **: IPP request failed with status 1280

** (gnome-cups-manager:9646): WARNING **: IPP request failed with status 1280
```

any help would be greatly appreciated.

update: lsusb returns this
```
root@ubuntu:~# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:7104 Hewlett-Packard DeskJet 3420c
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

-Jeff

---

### Post by %hMa@?b&lt;C on 2005-12-04
tried it as not root. got this output
```
crowell@ubuntu:/root$ gnome-cups-manager Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gnome-cups-manager:11107): Gtk-WARNING **: cannot open display:
crowell@ubuntu:/root$

```

---

### Post by schdefan on 2005-12-04
are you connected with ssh to the machine. Is cupsd running?
> ps -A| grep cups
schdefan

---

### Post by %hMa@?b&lt;C on 2005-12-04
[QUOTE=schdefan]are you connected witth to the machine. Is cupsd running?

schdefan[/QUOTE]
it is connected to the machine via usb
the output is
```
root@ubuntu:~# su crowell
crowell@ubuntu:/root$  ps -A| grep cups
13455 ?        00:00:00 gnome-cups-mana
13456 ?        00:00:00 gnome-cups-mana
13457 ?        00:00:00 gnome-cups-mana
crowell@ubuntu:/root$

```

---

### Post by schdefan on 2005-12-04
the cups daemon is not running!
run in a terminal 
> sudo /etc/init.d/cupsys restart
Normally the cups daemon is started at boot time.
If you need some more help write me a private message;) 
schdefan

---

### Post by %hMa@?b&lt;C on 2005-12-05
problem came back
```
crowell@ubuntu:~$  ps -A| grep cups
10648 ?        00:00:00 gnome-cups-mana
10685 pts/0    00:00:00 gnome-cups-mana
10714 ?        00:00:00 cupsd
10723 pts/1    00:00:00 gnome-cups-mana
10726 ?        00:00:00 gnome-cups-mana

```

---

### Post by %hMa@?b&lt;C on 2005-12-06
plesae i cant figure this out.... help

---

### Post by %hMa@?b&lt;C on 2005-12-06
the thing is that it works with a fresh install, but refuses to work after a reboot

---

### Post by schdefan on 2005-12-07
fresh ubuntu installation or just reinstalled cupsys?

---

### Post by %hMa@?b&lt;C on 2005-12-07
[QUOTE=schdefan]fresh ubuntu installation or just reinstalled cupsys?[/QUOTE]
fresh installation of the entire ubuntu 5.10 operating system

---

### Post by %hMa@?b&lt;C on 2005-12-11
bumperoo

---


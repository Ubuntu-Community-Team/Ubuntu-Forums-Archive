---
title: "configuring printer"
date: 2005-06-20
forum: Desktop Environments
---

### Post by blu_asrai on 2005-06-20
Hi.

I'm trying to configure the network printer, after I got the hoary release.

My first problem was I could not enter the cups web interface, as I
was not able to enter as root (i changed the /etc/cups/cups.conf: i renamed
the cupsys user by the root user).

I try with gnome printer administrator and i worked; i also could see the printer
I installed with cups.

The main problem is that I cannot print anything but the test page.
The error is:

lpr: error - scheduler not responding!



Any help?

Thanks!

---

### Post by shakin on 2005-06-20
[QUOTE=blu_asrai]Hi.

I'm trying to configure the network printer, after I got the hoary release.

My first problem was I could not enter the cups web interface, as I
was not able to enter as root (i changed the /etc/cups/cups.conf: i renamed
the cupsys user by the root user).

I try with gnome printer administrator and i worked; i also could see the printer
I installed with cups.

The main problem is that I cannot print anything but the test page.
The error is:

lpr: error - scheduler not responding!



Any help?

Thanks![/QUOTE]
 I suggest installing and using kcontrol to setup your printer. It's excellent.

---

### Post by blu_asrai on 2005-06-20
[QUOTE=shakin]I suggest installing and using kcontrol to setup your printer. It's excellent.[/QUOTE]
Thanks for the answer.

Anyway, kcontrol tells me that Printer daemon for KDE does not run,
and at the moment I have no idea how to manage this.

I'm  confused.

---

### Post by mrcbrown on 2005-06-20
[QUOTE=blu_asrai]Thanks for the answer.

Anyway, kcontrol tells me that Printer daemon for KDE does not run,
and at the moment I have no idea how to manage this.

I'm  confused.[/QUOTE]
 What printer are you trying to install? And are you using KDE or Gnome?

---

### Post by blu_asrai on 2005-06-20
[QUOTE=mrcbrown]What printer are you trying to install? And are you using KDE or Gnome?[/QUOTE]

The printer is a network printer, HP Laserjet 2300dn.
I'm using gnome.

---

### Post by cwaldbieser on 2005-06-20
In the terminal, what is the output of:

```
$ sudo ps -Al | grep cupsd
```

If it is blank, then the cupsd service is not running, and you will need to try to start it.  If it comes back with a process table entry like:

```
5 S   103 18047     1  0  86  10 -  1395 -      ?        00:00:00 cupsd
```

Then it is running.

Assuming it is not running, try:

```
$ sudo cupsd
```

If there is no error message, it is hopefully running at this point.  If there was an error message, or if it wasn't running, you might try:

```
$ dmesg
```

and report any errors related to cups you might find there.

---


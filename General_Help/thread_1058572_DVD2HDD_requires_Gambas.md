---
title: "DVD2HDD requires Gambas?"
date: 2009-02-03
forum: General Help
---

### Post by ToyotaGuy23 on 2009-02-03
I installed DVD2HDD.  
I cannot get it to run because it requires something called Gambas...

I went into synaptic, and downloaded the Gambas2 package, and the program STILL will not run.  

The error I get is 
'Could Not Launch Menu Item'
'Failed to execute child process /usr/bin/dvd2hdd.gambas 
(No Such File Or Directory)

**I DO** need to use this particular program

---

### Post by lykwydchykyn on 2009-02-03
Does the file "/usr/bin/dvd2hdd.gambas" exist?  Where did you get dvd2hdd and what directions did you follow to install it?

Gambas is a scripting language similar to BASIC.  Apparently your program is a gambas script, which is why Gambas is required.

---

### Post by ToyotaGuy23 on 2009-02-03
I installed the program from a 3rd party (website) download.
The /usr/bin/dvd2hdd.gambas does NOT exist.

I installed it from terminal do you need the exact commands?
The installation used something called autopackage, which asked for a password,(strange) but I clicked 'no password' and it installed.  

Here is EXACTLY what happened:
[http://paste.ubuntu.com/113058/](http://paste.ubuntu.com/113058/)

> **lykwydchykyn said:**
> Does the file "/usr/bin/dvd2hdd.gambas" exist?  Where did you get dvd2hdd and what directions did you follow to install it?

Gambas is a scripting language similar to BASIC.  Apparently your program is a gambas script, which is why Gambas is required.

---

### Post by TransitMan on 2009-02-03
Which version of Ubuntu are you using?

From what I've found, anything higher than 7.10 and DVD2HDD will not run. 
Further, it looks like development of it was termed in Dec 2006/Jan 2007.

---

### Post by todak on 2009-02-03
Use k9copy. If you do not want to pull KDE packages into your GNOME environment, then install WINE and use DVDshrink.

---

### Post by jrusso2 on 2009-02-03
> **TransitMan said:**
> Which version of Ubuntu are you using?

From what I've found, anything higher than 7.10 and DVD2HDD will not run. 
Further, it looks like development of it was termed in Dec 2006/Jan 2007.

I am running it on 8.04.  I don't remember where I got gambas from though, maybe from the download page for DVD2HDD?  Or maybe I searched and found it.

---

### Post by ToyotaGuy23 on 2009-02-03
Then that means that this DVD cannot be copied under Linux.
Not a playable copy anyway.
[http://www.i-hack.org/computer/other-components/how-copy-an-arccos-protected-dvd.html](http://www.i-hack.org/computer/other-components/how-copy-an-arccos-protected-dvd.html)

Even windows systems requrire like three tools to do it, and my VM won't recognize it quite right.  

Oh well, whatever.

---


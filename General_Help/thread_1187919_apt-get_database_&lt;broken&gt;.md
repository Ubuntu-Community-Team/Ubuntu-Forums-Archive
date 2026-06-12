---
title: "apt-get database &lt;broken&gt;"
date: 2009-06-15
forum: General Help
---

### Post by johnh10000 on 2009-06-15
Hi gang,

Before I reinstall everything, got any ideas how I could rebuild the apt-get database?

Everytime I access it, the box freezes.  Not good.

I've tried from the box it self (9.04):

sudo apt-get update
     apt-get upgrade
     aptitude upgrade
     apt-get -f install
     dpkg --configure -a
     apt-get upgrade

The problems started after I put bbci player on, their site installed it.

---

### Post by gradinaruvasile on 2009-06-15
U mean u installed a repository?

---

### Post by Soul-Sing on 2009-06-15
What is the exact error you get?

---

### Post by johnh10000 on 2009-06-15
> **leoquant said:**
> What is the exact error you get?

It just crashes with style.  The hard disk light stays on.  And the box does nothing the mouse stops no keylock light.  It happens to serve my website that stops too

---

### Post by johnh10000 on 2009-06-15
> **gradinaruvasile said:**
> U mean u installed a repository?

don't think so

---

### Post by lamego on 2009-06-15
An apt database corruption would not hang your system.
You must have a much more serious problem causing a kernel hang.
Please boot from a livecd and run a fsck on your root filesytem.

---

### Post by johnh10000 on 2009-06-15
> **lamego said:**
> An apt database corruption would not hang your system.
You must have a much more serious problem causing a kernel hang.
Please boot from a livecd and run a fsck on your root filesytem.

Ok remind me of the switches pls.

Also if I choose to reinstall, could I not format it and get away with it?

Ie I would like to put on server and desktop.

---

### Post by johnh10000 on 2009-06-15
Well reinstall - now working again.

---


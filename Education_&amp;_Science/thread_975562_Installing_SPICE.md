---
title: "Installing SPICE"
date: 2008-11-08
forum: Education &amp; Science
---

### Post by fredscripts on 2008-11-08
Hi!

I've read in a electrical engineering book that SPICE is a well-known software to simulate electrical circuits.

It isn't in Ubuntu 8.10 repositories, and googling points out to different packages and it's really annoying there's no official website with the latest release (or at least it isn't very clear).

Anyone know the best way to install the current stable version of SPICE?


Thanks so much in advance!

---

### Post by Nirva on 2008-11-08
sudo apt-get install easyspice

This is a graphical frontend for the electrical circuit simulator Spice. It is by default connected to the geda package and ngspice but can be used as a frontend for other spice simulators programs as well.

---

### Post by mitch_feaster on 2009-03-13
Anyone trying to install ngspice should check out [this guide]("https://electronics.wiki.usu.edu/ngspice_Install") and [this thread]("http://ubuntuforums.org/showthread.php?t=596831")

---

### Post by Guskuma on 2011-05-28
I've installed ngspice in my ubuntu, but now want to get rid of this.
How can i do it?

I have no idea of how to remove/uninstall this program.

Thanks!

---

### Post by el_koraco on 2011-05-28
how did you install it?

---

### Post by linuxford on 2011-09-15
```
sudo apt-get remove ngspice
```

---


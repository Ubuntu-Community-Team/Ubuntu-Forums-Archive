---
title: "Make my own version of Ubuntu"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Justin Holt on 2006-09-10
Alright, i've seen nUbuntu and Fluxbuntu, and i want to know how to do it. Is there a way to get my own ubuntu customized with what i want installed in it so i don't have to keep installing things like  java or flash. Is there anyway to do it?

---

### Post by Jussi Kukkonen on 2006-09-12
It's possible, but quite a lot of work. This is the quick approach: create your own meta-package that depends on all the stuff that you need. Then you'll only need to install your meta-package after installation.

[http://www.tldp.net/HOWTO/Debian-Binary-Package-Building-HOWTO/index.html](http://www.tldp.net/HOWTO/Debian-Binary-Package-Building-HOWTO/index.html)

---

### Post by Justin Holt on 2006-09-12
Thank you for responding...but how do i make a metapackage?

---

### Post by mhancoc7 on 2006-09-12
> **Justin Holt said:**
> Thank you for responding...but how do i make a metapackage?

The link that Jussi Kukkonen posted gives instructions on creating a simple metapackage.

If you actually want to make "your own ubuntu" you could try the [Ubuntu Customization Kit (UCK)]("http://uck.sourceforge.net/"), or [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1"). They allow you to create your own LiveCD. I use [UCK]("http://uck.sourceforge.net/") and it works well, but is lacking in documentation and has a bit of a learning curve. [Reconstructor]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1") is all GUI, but I have never been able to get it to work.

Hope that helps, Jereme

---

### Post by Justin Holt on 2006-09-12
thank you for everything...i tried to get to uck and it timed out...i will try it again

---


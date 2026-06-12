---
title: "How do I build a .deb for Ubuntu?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by ardchoille on 2005-11-27
I have built lots of packages for other distros, mainly rpm-based, and I'd like to learn how to build .deb packages for Ubuntu 5.10. Is there a how-to about this somewhere?

---

### Post by aysiu on 2005-11-27
Does [this thread](http://ubuntuforums.org/showthread.php?t=51003) help?

---

### Post by ardchoille on 2005-11-27
[QUOTE=aysiu]Does [this thread](http://ubuntuforums.org/showthread.php?t=51003) help?[/QUOTE]
Well, thanks for the link.. it's a great tutorial. But, I have no idea what cflags, compiling commands, clean commands, or installation commands are. Nor do I understand half of what that tutorial is talking about, so I guess I will be left out of this. I am glad that the Ubuntu repos have many packages :)

---

### Post by aysiu on 2005-11-27
So is your question really "How do I install stuff that's not in the repositories?" and not "How do I build a .deb for Ubuntu?" If so, see: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by ardchoille on 2005-12-02
[QUOTE=aysiu]So is your question really "How do I install stuff that's not in the repositories?" and not "How do I build a .deb for Ubuntu?" If so, see: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)[/QUOTE]
No, my question was actually, "how do I build a .deb for Ubuntu" because I wanted to build my own packages so the package manager can manage them instead of building from source and managing them myself. I just need to find the patience-1.0 package :)

---

### Post by teaker1s on 2005-12-02
alien will change rpm to .deb

---

### Post by suoko on 2005-12-02
also try checkinstall...
it can create a deb package from source packages.
Just do ./configure and then run checkinstall as root

---

### Post by Chris_(medico_2001) on 2005-12-02
[QUOTE=suoko]also try checkinstall...
it can create a deb package from source packages.
Just do ./configure and then run checkinstall as root[/QUOTE]

I believe it is:
./configure
make
and then checkinstall.

Take a look at [kconfigure](http://kconfigure.sourceforge.net/) if you would like a GUI frontend to build the package (you will still need to install checkinstall)

---

### Post by ardchoille on 2005-12-10
Thank you for the replies.. lots of good stuff there. I love these forums!

---


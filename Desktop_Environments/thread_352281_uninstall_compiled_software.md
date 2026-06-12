---
title: "uninstall compiled software"
date: 2007-02-03
forum: Desktop Environments
---

### Post by gaillard on 2007-02-03
Hi I installed kiba-dock from their source on their site but it is not working correctly (Beryl user here) at least I dont think so.  I followed their directions in their install file but perhaps someone knows a trick.  I also have a .deb file for kiba and AMD64 on my desktop that I found after I did the compile and install.  How do I remove what I installed and try the deb?

Just so you guys know what it is doing, its not displaying correctly, all jarbeled sorta.

Thanks for the help.

---

### Post by igknighted on 2007-02-03
How did you install it?  Did you use checkinstall to make a quick .deb or did you just install via the compile?  If you just compiled, do you still have the source and makefile leftover that you compiled from?

---

### Post by gaillard on 2007-02-03
ya here is what it said to do, which I did

./autogen.sh
make
make install-schemas
make install (as root)

And I do have the source

---

### Post by gaillard on 2007-02-03
Any ideas? I know this is pretty simple...

---

### Post by melancholeric on 2007-02-03
Well, the binary probably ended up to /usr/local/bin. Config files might be in /usr/local/etc. Libraries, if there were any, are probably in /usr/local/lib. Now, you might be able to just delete them, then remove possible menu entries ... and it should be gone.

not that I've ever tried that and I might actually be completely wrong and your computer may explode if you do this. And worst of all, someone will correct me on this.

---

### Post by raul_ on 2007-03-01
Stumbled on this post. go to the directory where you did "make install" and try making "make uninstall". Try reading the software documentation and see if it says something about uninstalling.

---


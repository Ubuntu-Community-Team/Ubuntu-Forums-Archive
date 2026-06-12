---
title: "Creating a .deb file from python source code?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by CPUFreak91 on 2005-12-09
I've downloaded PGU 0.9 for pygame and python2.4 but I can't install it (I'm told that   /usr/lib/python2.4/config/Makefile doesn't exist).... how can i make a *.deb file out of it?

All it is is source code inside a tar.gz file (I tried alien but it didn't work.. [DUH!])

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=CPUFreak91]I've downloaded PGU 0.9 for pygame and python2.4 but I can't install it (I'm told that   /usr/lib/python2.4/config/Makefile doesn't exist).... how can i make a *.deb file out of it?

All it is is source code inside a tar.gz file (I tried alien but it didn't work.. [DUH!])[/QUOTE]
Are there README and INSTALL docs that came with it?

There is a sub-forum that discussed how to package stuff for Ubuntu, but I was thinking that it may just be easier to write a simple makefile that would do the install, then you could use checkinstall.

If I knew what files had to go where, I could probably explain how you could create the makefile.

---

### Post by CPUFreak91 on 2005-12-29
Well I'm trying to install Phil's Pygame Utilities. There are no debian files on the sourceforge download.

---

### Post by cwaldbieser on 2005-12-29
[QUOTE=CPUFreak91]Well I'm trying to install Phil's Pygame Utilities. There are no debian files on the sourceforge download.[/QUOTE]
OK, I downloaded the tarball, and I wrote a pretty simple makefile for it.  Make sure you have checkinstall installed (via apt-get or synaptic).  Copy the makefile into the project directory, cd into that directory, and then issue these commands:

```

$ make
$ sudo checkinstall -D

```
There will be some prompts for you to fill out (like what you want to call the package).  You can leave defaults for most of them.  The checkinstall program will create the .deb for you and install it.

The makfile is attached.   Let me know how it goes.

---

### Post by cwaldbieser on 2005-12-29
For some reason the makefile did not attach-- it should be here.

---

### Post by CPUFreak91 on 2006-01-21
thank you with a little editing this does the trick

---


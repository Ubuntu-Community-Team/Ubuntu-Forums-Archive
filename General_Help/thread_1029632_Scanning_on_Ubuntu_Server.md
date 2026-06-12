---
title: "Scanning on Ubuntu Server"
date: 2009-01-03
forum: General Help
---

### Post by {}dif{} on 2009-01-03
Hi all,

I'm having trouble getting a scanner to work remotely from Ubuntu server.

**Setup:**
I have a laptop that the video no longer works on so I'm making it a dedicated VM server.  I have a VM (using KVM) setup for printer sharing.  Since I have an all in one printer it means that I need to share the scanner via the server as well.  (I would put it on my desktop and share the thing there but I want to start shutting down my desktop and the printer needs to be available to everyone else.)

Anyway, the server is a JeOS 8.04 VM (Ubuntu 8.04 Server host).  Aside from cups for printing and a few other general utilities, I've installed sane-utils and libsane.  I followed the following page for setting up the server using xinetd: [https://help.ubuntu.com/community/ScanningHowTo#Server-side%20Setup](https://help.ubuntu.com/community/ScanningHowTo#Server-side%20Setup).

**Problem:**
On the server, when I `scanimage -L`, it doesn't find the scanner, but when I `sudo scanimage -L` it finds the scanner just fine.  The attached file is the output of those two as well as `lsusb -v` and `sudo lsusb -v`.  It also has `ls /dev`.  The user I've done this with is in the scanner group so I'm not exactly sure why the permissions are disallowing it without sudo.  Any help fixing the permissions would be greatly appreciated!  Let me know if there's any more information needed!  Thanks in advance.

---

### Post by CrusaderAD on 2009-01-03
The chmod command will adjust any permissions. I actually installed a desktop on top of the server edition.

```
sudo apt-get install ubuntu-desktop
```

You can install other types too... like xubuntu-desktop or kubuntu-desktop. Having a GUI makes it much easier in setting up network components in my opinion.

---

### Post by {}dif{} on 2009-01-03
Hey,

Thanks for the reply.  Unfortunately that isn't an option.  Since its a VM I have very limited RAM and disk space for that matter and I don't really want to use either resource any more than I need to.

I know this is something that should work.  Maybe it's actually a bug?  (Since users in the scanner group aren't able to actually access the scanner)  I forget where but I thought I saw that consolekit fixed the problem but again that takes more resources than should be necessary.  Anyone know any more about this.  Much appreciated!

---


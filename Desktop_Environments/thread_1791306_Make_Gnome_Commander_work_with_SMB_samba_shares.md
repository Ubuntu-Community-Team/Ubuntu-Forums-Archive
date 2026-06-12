---
title: "Make Gnome Commander work with SMB samba shares"
date: 2011-06-26
forum: Desktop Environments
---

### Post by John Bennett on 2011-06-26
Gnome Commander seems to interact with Windows shares much better than the default Natty file manager Nautilus.

Gnome Commander is available in the Ubuntu Software Center.

Even after following dmizer's wonderful "Howto: Fix Windows share browsing issues" located here  [[link]]("http://ubuntuforums.org/showthread.php?t=1169149"), I was still having problems with dropped transfers and slow speeds.

Using Gnome Commander and installing the package *libgnomevfs2-extra* seemed to fix this.

[http://packages.ubuntu.com/natty/libgnomevfs2-extra](http://packages.ubuntu.com/natty/libgnomevfs2-extra)

---

### Post by SimonBishop on 2011-10-23
You are the man!!!!

---

### Post by bluurgh on 2012-08-02
After searching for a cure for Gnome Commander's annoying "Failed to browse the network. Is the SMB module installed?" notification, I found this thread and decided, hey ho, let's go.

Installing libgnomevfs2-extra fixed this error. Thanks very much for this tip John!

It was only then that I found out Gnome Commander cannot use the "Synchronize Directories" command on remote directories ("Operation not supported on remote file systems"), so I'll try something else for that...

---

### Post by Peter Wagner on 2012-08-11
Hello, you are indeed the man, I got the problem, googled "gnome commander samba", got this thread, copied the name to the software center, INSTALL, and it ran.

---

### Post by Yoast on 2012-12-25
I just came across this excelent explanation too. I have used Gnome commander for a while with the oaccasional problem and this should help overcome those problems.
Thanks.
Y.

---


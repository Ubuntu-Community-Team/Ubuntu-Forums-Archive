---
title: "gcc question?"
date: 2006-01-13
forum: Desktop Environments
---

### Post by Razorback on 2006-01-13
I am following a how to guide for installing my modem.  It is needing gcc 3.4 but I already have gcc 4.0.  Is it ok to have both installed or will it cause problems having both? Thanks.

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=Razorback]I am following a how to guide for installing my modem.  It is needing gcc 3.4 but I already have gcc 4.0.  Is it ok to have both installed or will it cause problems having both? Thanks.[/QUOTE]
It's ok with gcc 4.0. :)

---

### Post by invalid on 2006-01-13
It is perfectly fine to have both, yes.

---

### Post by qferret on 2006-01-14
I have both installed. Ubuntu (at least on my box) seems to use a symlink at /usr/bin/gcc to point to the default gcc for the system. I just change the symlink from the 3.4 to the 4.0 binary, depending on what I'm compiling....

---

### Post by Razorback on 2006-01-15
Noob question:  What is a symlink?

---

### Post by qferret on 2006-01-17
symbolic link

"ln -s <target> <link name>

basically a "shortcut" in Windows terms

---

### Post by Razorback on 2006-01-17
Thanks.  When you do this, does that make the link permanent or until you shutdown the pc.

---

### Post by Ameet on 2006-01-17
[QUOTE=Razorback]Thanks.  When you do this, does that make the link permanent or until you shutdown the pc.[/QUOTE]

The link stays until you remove it.  The distinction is between a symbolic link (which we are discussing here), and a "hard link".  The symbolic link is a little file that "points" to the file it is linking to.  A hard link (use command "ln" without the "-s" option) points directly to the same file node as the original file.  They are two different directory entries to the same file.  For that reason, a hard link has to be on the same file structure (same partition); but a symbolic link can point to a file on another partition or drive with ease.

Other experts please correct me if I got it wrong! ;)

---

### Post by qferret on 2006-01-17
[QUOTE=Ameet]The link stays until you remove it.  The distinction is between a symbolic link (which we are discussing here), and a "hard link".  The symbolic link is a little file that "points" to the file it is linking to.  A hard link (use command "ln" without the "-s" option) points directly to the same file node as the original file.  They are two different directory entries to the same file.  For that reason, a hard link has to be on the same file structure (same partition); but a symbolic link can point to a file on another partition or drive with ease.

Other experts please correct me if I got it wrong! ;)[/QUOTE]

That, & hardlinking doesn't allow a different name. The link is the same filename as the original. Symlinks can be named differently, so the symlink "gcc" can point to the binary "gcc3" or "gcc4", depending on which you set as the target when creating the link.

---


---
title: "Permission Denied?"
date: 2005-08-04
forum: Desktop Environments
---

### Post by kyotodude on 2005-08-04
Using the terminal in GNOME, I tried to change the display manager from KDM to GDM, but when I try to reconfigure I get this:

kyotodude@ubuntu:~$ sudo dpkg-reconfigure kdm
Password:
sudo: unable to execute /usr/sbin/dpkg-reconfigure: Permission denied

What does this mean?  It worked before!  I know my password is right.
Thanks!

---

### Post by evilghost on 2005-08-04
What do your permissions look like on that file, here are mine:

```

luser@400sc:~$ stat /usr/sbin/dpkg-reconfigure
  File: `/usr/sbin/dpkg-reconfigure'
  Size: 3336            Blocks: 8          IO Block: 4096   regular file
Device: 301h/769d       Inode: 8569136     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2005-08-02 17:48:37.000000000 -0500
Modify: 2005-03-01 16:08:07.000000000 -0600
Change: 2005-07-22 18:14:32.000000000 -0500

```

---


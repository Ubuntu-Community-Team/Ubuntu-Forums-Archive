---
title: "[SOLVED] Increasing Ubuntu file size"
date: 2008-12-31
forum: General Help
---

### Post by Sunspore on 2008-12-31
Hi, my Ubuntu was install in vista using NTFS file system, in the initial installation I only allocate 10GB for Ubuntu. Now I am using Ubuntu more often than my Vista on my laptop as Ubuntu is so much faster. I would like to increase the file size to 30GB

I would like to know how can I increase my file size as I tried that inside ubuntu and they did not detect the file as it was install in NTFS system.

If possible I would like to increase the file size and also convert the the current Ubuntu NTFS file structure to Linux file structure with all information intact. 

Wonder if it is too much to ask. 

Thank You.

---

### Post by oldos2er on 2008-12-31
Did you do a Wubi install?

---

### Post by Sunspore on 2008-12-31
Hi, I install using the previous . I think is 8.02. I remember just downloading the iso, burn in, log in to vista and install from there. This Ubuntu auto load from wubi but I am not sure as it is a few months back.

:-)

---

### Post by prshah on 2008-12-31
> **Sunspore said:**
> 
I would like to know how can I increase my file size as I tried that inside ubuntu and they did not detect the file as it was install in NTFS system.


Looks like you have a wubi (within windows) installation.

Take a look at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

See the section on "Resizing virtual disks using LVPM"

You can also read up (from the same link) on how to move your installation to a dedicated partition; this will give you a slight speed boost, as well as prevent problems in Vista from affecting your Ubuntu installation.

---

### Post by Sunspore on 2008-12-31
Thanks, I will give it a try.

---


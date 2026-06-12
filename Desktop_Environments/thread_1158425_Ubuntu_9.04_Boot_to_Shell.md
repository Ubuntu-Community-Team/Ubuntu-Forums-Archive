---
title: "Ubuntu 9.04 Boot to Shell"
date: 2009-05-13
forum: Desktop Environments
---

### Post by Muki on 2009-05-13
Does anyone know how to boot into the shell instead of the X GUI? I would like to boot into the shell, and then launch the GUI later. Tried one way that I read about in Beginning Ubuntu Linux 3rd ed, but that didn't work on Ubuntu 9.04.

Any ideas?

---

### Post by pro003 on 2009-05-13
there is a option if you get into Recovery mode, then drop to root shell.

from there you can start x session with command **startx**

---

### Post by Muki on 2009-05-13
Thanks. It was no problem to get in to the shell, as you explained, pro003. But that put me in as root. From there, when I typed startx, I was brought into the GUI but had some error messages and the machine froze up. Tried a second time changing user to my usual user account before i typed startx, but this time as well, I had error messages, and the big freeze.

Anyone else?

In the Beginning Ubuntu Linux book I mentioned in my first post, there is an explanation of how to do this by deleting the S13GDM file in /etc/rc3.d, and adding "id:3:initdefault:" to a newly created inittab file. But this does not work.

In my installation, there is no /etc/rc3.d/S13GDM file at all.

---

### Post by pro003 on 2009-05-13
if you are a root try logout, just typing 'logout', am not sure its gonna give you yourname@ubuntu:~#
and then startx should work

but if you don't want to boot into graphic mode, you should: 

1. Remove the symlink(s) from your rc dir, which are starting the
"graphical programs".
2. Change the default runlevel in your /etc/inittab. 
(which is not a good idea if you ask me, only do this if you know what you're doing).

3. You might want to look in /boot/grub/grub.conf

In the kernel line you see a splash getting loaded, simply remove that part of the line.
You can also remove the quiet flag if you want to see more output.

the last option is most likely to work, but be sure to make a backup of menu.lst in /boot/grub/

---


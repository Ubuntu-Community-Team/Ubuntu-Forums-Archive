---
title: "Installing a kernel?"
date: 2005-07-07
forum: Desktop Environments
---

### Post by adamb10 on 2005-07-07
I want to upgrade my kernel the easy way.  Is there a way to skip the kernel config  or something?

---

### Post by Lunde on 2005-07-07
[QUOTE=adamb10]I want to upgrade my kernel the easy way.  Is there a way to skip the kernel config  or something?[/QUOTE]
 I think you need to be more spesific, do you want to upgrade to 2.6.12? If so it's a howto here by** luca_linux**:
[http://www.ubuntuforums.org/showthread.php?postid=221149#poststop](http://www.ubuntuforums.org/showthread.php?postid=221149#poststop)

Some more links:
[https://wiki.ubuntu.com//KernelCompileHowto](https://wiki.ubuntu.com//KernelCompileHowto)
[http://www.ubuntuforums.org/showthread.php?t=42714](http://www.ubuntuforums.org/showthread.php?t=42714)

Be careful I would recomend doing a backup of your system first like this howto by **Heliode**:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by adamb10 on 2005-07-07
[QUOTE=Lunde]I think you need to be more spesific, do you want to upgrade to 2.6.12? If so it's a howto here by** luca_linux**:
[http://www.ubuntuforums.org/showthread.php?postid=221149#poststop](http://www.ubuntuforums.org/showthread.php?postid=221149#poststop)

Some more links:
[https://wiki.ubuntu.com//KernelCompileHowto](https://wiki.ubuntu.com//KernelCompileHowto)
[http://www.ubuntuforums.org/showthread.php?t=42714](http://www.ubuntuforums.org/showthread.php?t=42714)

Be careful I would recomend doing a backup of your system first like this howto by **Heliode**:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)[/QUOTE]
 What I am wondering though, when I do the new kernel will the stuff that Ubuntu set up in the kernel be there?  I don't want to go through the kernel customization. I just want the newest kernel with ubuntu defaults like it is during a fresh install of Ubuntu.

---

### Post by Lunde on 2005-07-07
[QUOTE=adamb10]What I am wondering though, when I do the new kernel will the stuff that Ubuntu set up in the kernel be there?  I don't want to go through the kernel customization. I just want the newest kernel with ubuntu defaults like it is during a fresh install of Ubuntu.[/QUOTE]
 Open a terminal window and type without the $:
$ uname -a
And post the output here

No matter what you do with your kernel, if you have kompiled something for the kernel before, you may have to do it again. But let's first see which kernel you have now with the above command

---

### Post by dewey on 2005-07-07
using $sudo apt-get dist-upgrade will give you the latest kernel officially released by ubuntu for hoary.  If you want a specialised kernel, such as k7,k8,or 686, search the forums, I've posted many times how to obtain them.

And yes, you skip kernel configuration when using an official ubuntu kernel.

---


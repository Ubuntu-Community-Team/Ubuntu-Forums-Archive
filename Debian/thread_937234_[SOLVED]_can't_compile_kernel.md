---
title: "[SOLVED] can't compile kernel"
date: 2008-10-03
forum: Debian
---

### Post by alvare on 2008-10-03
Hi, it's my first time posting here. I think I am an advanced Linux user (know some awk, perl, php, C++, python, sed and bash) and I am Argentinian, so excuse my english (i don't post in ubuntu espanish because i never really found a solution there).

When I upgraded to kernel 2.6.26 I found a bug where when switching between X and VTs or when quitting X my arrow keys just stop working, I tryied some alt+petsis+r and killing proceses but they had just disappear completely.

Well so I tryied to compile my own kernel 2.6.26, but when booting, it says something like "pernel panic: VFS unable to mount" or "unknown type"
and my bloq-num and scroll-lock keys titilate.

I got tired of compiling with the defaults, with the "working" 2.6.26 one config, with my config and with the working 2.5.25 config but it was all useless.

So in short it is: some kernel panic when compiling and the arrow keys disappearing when switching VTs and X with KDE.

PS: I am using a Debian lenny with a IDE hd and a Intel CeleronD 2.6 at 3.2 GHz (in case overclocking can affect)

Will appreciate any help, xP

---

### Post by InfinityCircuit on 2008-10-03
Debian has not made the libata transition.  Try switching your /dev/hdXs to /dev/sdXs in /boot/grub/menu.lst and /etc/fstab.

Remember that this is ubuntuforums.org, so if you want specific Debian help, you might want to consider forums.debian.net

---

### Post by alvare on 2008-10-04
thanks, will try...
i asked here because it's the best place i've ever seen about linux questions, some people know very much and you always get an answer.

---

### Post by VMC on 2008-10-04
> **alvare said:**
> Well so I tryied to compile my own kernel 2.6.26, but when booting, it says something like "pernel panic: VFS unable to mount" or "unknown type"
and my bloq-num and scroll-lock keys titilate.

I got tired of compiling with the defaults, with the "working" 2.6.26 one config, with my config and with the working 2.5.25 config but it was all useless.How did you compile it? Where did you get your ".config" file from or did you just create it from scratch. Sometimes the "Linux Kernel panic: VFS: Unable to mount root fs" is you didn't include the correct FS. Is your ext2/ext3?

---

### Post by alvare on 2008-10-04
i compiled it with the 2.6.25 config, the 2.6.26 config and from scratch

xP...maybe some bad luck

---

### Post by VMC on 2008-10-05
run make xconfig and recheck the section "File systems". Make sure Ext2/Ext3 and enabled.

---

### Post by alvare on 2008-10-05
i checked that like a thousand times before..thanks anyway

yesterday i runned update-initramfs and the kernel panic desapeared ! 
but ti shows a couple of messages about enumerating usb devices ( which all kernels show) and it stops completely there...

maybe waiting for the 2.6.27 is the best choice :)

---

### Post by mohitchawla on 2008-10-05
^^You might wanna wait after its done with the USB devices. Give it around three minutes. I had some similar issue on my Classmate clone, and the only fix I found was to wait.

---

### Post by alvare on 2008-10-11
YEAH I WON !!! :):):):):)
I compiled 2.6.27 and changed all /dev/hdX for /dev/sdX and it works fine !

Thank you guys...:lolflag:

PS: Why the heck did they changed hdX for sdX ?? I thought sdX was for scsi devices or something like that

---


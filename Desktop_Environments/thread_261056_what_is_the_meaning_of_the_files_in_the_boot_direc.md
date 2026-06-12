---
title: "what is the meaning of the files in the /boot directory"
date: 2006-09-19
forum: Desktop Environments
---

### Post by zigi on 2006-09-19
can someone explain it to me?

thx

---

### Post by kidders on 2006-09-19
Hi there,

The files in /boot are involved in ... well ... booting your machine. The most important is the Linux kernel itself, called something like "vmlinuz" on many systems. Quite often, people like to include a copy of the configuration file used to generate the kernel in /boot as well.

Most Ubuntu systems also use a thing called an initrd (initial ramdisk) image ... the explanation for what that does is quite involved, so post back if you *really* want to know lol!

That's the **brief** explanation ... post back if you'd like more, or maybe take a wander around a few search engines. I suppose the most important thing to mention is that you should absolutely never touch anything in /boot unless you know exactly what it does ... even the slightest error can make your system fail to boot.

---

### Post by nullmind on 2006-09-19
The grub directory has the configuration files that are involved with the menu you most likely see when your machine starts up (the GRUB loader). Changing these files lets you change how the system will boot up, or what options you have (ie: like Windows, or other secondary OS's)

A good example is the /boot/grub/menu.lst. I don't think you should change it without reading about it more, because it might make the system hard to boot.

---

### Post by zigi on 2006-09-28
ok, can you be more accurately?

ls -l /boot

-rw-r--r-- 1 root root  266735 2006-09-16 05:47 abi-2.6.15-27-386
-rw-r--r-- 1 root root   69967 2006-09-16 03:49 config-2.6.15-27-386
drwxr-xr-x 3 root root    1024 2006-09-26 20:54 grub
-rw-r--r-- 1 root root 6754446 2006-09-26 20:54 initrd.img-2.6.15-27-386
-rw-r--r-- 1 root root   94760 2005-10-25 12:32 memtest86+.bin
-rw-r--r-- 1 root root  725967 2006-09-16 05:48 System.map-2.6.15-27-386
-rw-r--r-- 1 root root 1414742 2006-09-16 05:47 vmlinuz-2.6.15-27-386

I know, what these files mean:

config-2.6.15-27-386 .. configuration file of the linux (kernel)
grub .. directory with configuration files for grub (linux loader)
initrd.img-2.6.15-27-386 .. image of modules needed "during" boot
memtest86+.bin .. image of the memtest86+ program (RAM memory test)
vmlinuz-2.6.15-27-386 .. image of self linux kernel

I don't know, what these files mean:

abi-2.6.15-27-386 .. ??
System.map-2.6.15-27-386 .. ??

---

### Post by kidders on 2006-09-29
Hi again,

System.map has to do with the kernel symbol table. Most modern Linuxes use /proc/ksyms to get hold of kernel symbol information though.

Afaik, ABI is a kernel patch that allows you to run non-Linux binaries.

---

### Post by zigi on 2006-10-25
I try compile my own kernel but I have these two problems:

1. It seems that framebuffer doesn't work .. only black screen after boot and than KDE

2. I don't know how to generate abi file for my kernel

---

### Post by kidders on 2006-10-25
It can be a little tricky to get fb support working sometimes. Could you post the relevant parts of your kernel config maybe, so we can see what you've done?

---

### Post by zigi on 2007-02-09
Hi, I try compile my own kernel. Everything went well, but size of my initrd.img is >17MB and size of initrd.img to distribution's kernel is cca 6,5MB. How is it possible? In /etc/initrams-tools configuration is setting in to most used modules.

---

### Post by kidders on 2007-02-09
Hey again,

There are lots of reasons why that might have happened. For example...

[LIST]
[*]You might have used a less efficient compression algorithm than the one used by your previous configuration.
[*]The image might contain lots more modules.
[*]The image could include very elabourate splash images, etc.
[*]A combination of the above.
[/LIST]

When I compile kernels, I don't usually use an initial RAMdisk, so I don't have a great deal of experience creating them. My best suggestion is to compare the 6.5MB & 17MB images, to see what changed. Take a look at the file types of the images themselves (**file** can help you with that) and the lists of files contained in each initrd. Perhaps something obvious will jump out at you!

---

### Post by zigi on 2007-02-09
Thanks for your fast reply. It is odd, because the same configuration is used to generate initrd.img for distributions kernels (I try update-initrams for all).

---

### Post by zigi on 2007-02-09
And I still don't know how to get the abi file.

---

### Post by kidders on 2007-02-09
Hmmm.... I wonder if nullmind is still watching this thread. He might be able to help out. If anything else occurs to me, I'll be sure to post back.

---


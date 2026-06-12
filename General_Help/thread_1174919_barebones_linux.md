---
title: "barebones linux"
date: 2009-05-31
forum: General Help
---

### Post by cmay on 2009-05-31
hi
i would like to know if there is a barebones linux distribuiton other than tiny core or linux from scratch . 

i would like to have a small system, on a usb stick  and it has to be absolute minimal. i have not found out yet if it is possible to just copy a kernel and shell along with  a home directory and use syslinux to mae it boot but it something as minimal as that i am looking for. 

any pointers would be great. 
thanks.

---

### Post by WatchingThePain on 2009-05-31
Arch Matey.

---

### Post by steeleyuk on 2009-05-31
Puppy Linux is quite barebones in terms of what it runs on and requires but it has a lot of programs installed by default.

To get pure minimum you could try compiling everything with Gentoo or starting with Arch.

Its not just a case of copying the kernel because you'll need the GNU programs and other bits and bobs which make a distro.

---

### Post by cariboo on 2009-05-31
If you don't need a gui, installing the cli from the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") takes up about 650MB.

---

### Post by cmay on 2009-05-31
> **cariboo907 said:**
> If you don't need a gui, installing the cli from the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") takes up about 650MB.
this is the iso image i use now always. i was happy when i found it as i use openbox and i always used the debian small iso images also. 

could i somehow have it boot from a usb sticjk using syslinux and the remove some things also. i want anhoter shell. and some custom programs and nothing more and running from a usb stick. 

its sort of a attemt to create the same environment as the linux from scratch livecd. 
it will serve almost the same purpose at the end also. 

its just  a small hobby project of mine. :) 

the idea is to have a partion of running linux system and the a partion of lots of sources so i can easy use the same usb stick to carrie both my usb system and my sources for programs that i can have running on both solaris and linux providing i can compile it from source. which means that i have to be able to use the usb stick as a container to hold boht a small minimal  live system and just to keep packages and pictures and sources and some few other files i can transport betwwen different systems. or use the live system as is . 

so if i install it on a usb stick with two partions will i not need to have syslinux as bootloader so it can boot if needed or do i need to figure out to install grub on the usb stick.

---

### Post by arubislander on 2009-05-31
> **cariboo907 said:**
> If you don't need a gui, installing the cli from the [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") takes up about 650MB.

For that you'd need at least a 1 GB stick. If you're going to use such a beast, why not use the USB Startup Disk Creator that comes with every new Ubuntu version (since 8.10 if I'm not mistaken) and boot it in persistent mode?

---

### Post by ChrisB111 on 2009-05-31
[Slax]("http://www.slax.org/") is a good choice and very small.

Chris

---

### Post by cmay on 2009-05-31
> **arubislander said:**
> For that you'd need at least a 1 GB stick. If you're going to use such a beast, why not use the USB Startup Disk Creator that comes with every new Ubuntu version (since 8.10 if I'm not mistaken) and boot it in persistent mode?
i already tried to do this wiht the linux from scratcht cd and i also tried unetbootin and both fails. 

i still want to make it even smaller than the linux from scratch cd is if possible and maybe want to use another shell. i want the c shell or ash instead of bash. 

ash is the shell used in minix and i like that. the c shell i am thinking about is the one bsd use as login shell . i never really giving that much thought before but i would like to use eihter one of them instead.

---

### Post by Jose Catre-Vandis on 2009-05-31
SLiTaz is another "small" option - full GUI experience inside 30mb, but probably not what you are looking for. I would go for Arch - but that is @ 360mb installed.

---

### Post by cmay on 2009-05-31
> **ChrisB111 said:**
> [Slax]("http://www.slax.org/") is a good choice and very small.

Chris
i know that one. its a great way to make a cd. 

what i want is to learn linux from scratch but running from a usb stick and still have some space left for carrying some other things i use on all my computers. my usb stick should be both used for holding stuff as useal use but also work as a running small linux from scracth cd.

---


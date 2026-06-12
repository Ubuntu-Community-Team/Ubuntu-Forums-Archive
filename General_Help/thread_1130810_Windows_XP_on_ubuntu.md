---
title: "Windows XP on ubuntu"
date: 2009-04-20
forum: General Help
---

### Post by MoeyO on 2009-04-20
Hi, just wondering if i can get some help.

Im a new user to Ubuntu and still slowly gaining knowledge on how to's.

Now ive installed Ubuntu as a dual boot with windows xp sharing the same drive. Is it possible to run my current windows xp on ubuntu with virtual box without having to reinstall windows?????

---

### Post by jimmyhacker on 2009-04-20
you can make a copy of your current installation of Windows with Qemu and you can run it so.

---

### Post by James_Lochhead on 2009-04-20
> **MoeyO said:**
> Hi, just wondering if i can get some help.

Im a new user to Ubuntu and still slowly gaining knowledge on how to's.

Now ive installed Ubuntu as a dual boot with windows xp sharing the same drive. Is it possible to run my current windows xp on ubuntu with virtual box without having to reinstall windows?????

I *believe* this is possible with VirtualBox (see Virtualization forum mega thread sticky). However, I tried to do this as well and it seems it is a very experimental feature... it is not really worth it in terms of risk vs reward.

---

### Post by FaizanKazi on 2009-04-20
Just in case you want some extra info: 
You have 3 major virtualization softwares: VirtualBox, VMWare and QEMU.
I've tried them all recently, and must say QEMU was the slowest, with the most memory usage. VirtualBox seems to allocate ALL the specified memory immediately, but after installing the "VirtualBox Additions" into the Guest machine it was definitely the best of the three: speed is very good and i love the mouse pointer integration so your dont have to completely surrender the mouse to the Guest OS and the dynamic window resizing/full screen/seamless display. VMWare is the fastest (but barely) and allocates memory as required (or so it seems), unfortunately i hate using it because its not as easy to use or set up if you still want some control over everything.

so it seems youre geared towards virtualbox. if youre sure about using VBox then try this:

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

OR:

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

also, i think you might have a HAL (hardware abstraction layer) problem... windows xp doesnt like it when hardware changes in a big way, so when you port your existing installation to VBox you might need some help:
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

happy vm-ing!! :)

> **MoeyO said:**
> Hi, just wondering if i can get some help.

Im a new user to Ubuntu and still slowly gaining knowledge on how to's.

Now ive installed Ubuntu as a dual boot with windows xp sharing the same drive. Is it possible to run my current windows xp on ubuntu with virtual box without having to reinstall windows?????

---

### Post by James_Lochhead on 2009-04-20
Depends if you mean the free (money) or paid version of VMware. I find VMware workstation guests far more stable than virtual box. Ofc VMware workstation is not cheap.

---

### Post by FaizanKazi on 2009-04-20
Yeah, Ive tried Vmware workstation and its pretty awesome. But honestly, i dont know what you mean by "more stable" because I have never had a single problem with VBox guests, actually, it supports more OS's (windows 7 beta, Ubuntu Jaunty Jackalope 9.4) out of the box (windows 7 beta didnt work in VMware).

I use a combination of VMware server or [www.easyvmx.com](www.easyvmx.com) (create only!) to manage / create my Virtual images and VMware player to run the guest OS's. Player is pretty awesome! So its just a little bit of switching back and forth between player and server whenever i wanna change something... pretty easy, but a little irritating.

> **James_Lochhead said:**
> Depends if you mean the free (money) or paid version of VMware. I find VMware workstation guests far more stable than virtual box. Ofc VMware workstation is not cheap.

---


---
title: "Install issues"
date: 2012-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by daisydew on 2012-07-17
I have a Dell Inspiron 1501 that had Vista installed. Didn't want it so installed Ubuntu9.04 disk.  It wiped out Vista and now I cannot open anything. I always get a archive error. No wireless. Cannot reinstall Vista.  Cannot uninstall Ubuntu. Cannot reinstall ubuntu. Cannot wipe hard drive and start over.  Dos  boot will not work.  Goes back to Ubuntu. Ran problem report.
Source Pack
   yelp
Package
   yelp2.25.1-ubuntu
Package architecture
   i386
Problem type
   Bug
Architecture
   i386
Proc Environ
   Lang=en_US.UTF-8
   Shell=/bin/bash
U name
   Linux 2.6.28-11 generic i 686
Distro release
   ubuntu 9.04
Prostatus
Date 
   tue.july 17 06 44.23 2012
Excutable path
   /us/bin/yelp
Computer now in worthless state.  What can I do?

---

### Post by Cheesehead on 2012-07-17
Please describe exactly what happens when you power on the system. Blinking lights? Beeps? Screen colors? Screen flickers? Error messages?

---

### Post by sudodus on 2012-07-17
Welcome to the Ubuntu Forums :-)

There are many people around willing to help. If you have time and are prepared to test a few things, I think we can help you to get your PC running with some version and flavour of Ubuntu.

1. Let us check about your computer: according to the specs in this link: [[COLOR="Red"]_http://www.laptopmag.com/review/laptops/dell-inspiron-1501.aspx#specs_[/COLOR]]("http://www.laptopmag.com/review/laptops/dell-inspiron-1501.aspx#specs")
CPU: 1.79-GHz AMD Turion 64 X2 Dual-Core TL-56
RAM: 1 GB (upgradable to 2 GB) Do you remember how much it is?
Graphics: ATI Radeon Xpress 1150
HDD: 80GB

2. Operating system: Ubuntu 9.04 has passed end-of-life, there are not even security updates now. Since the hardware is fairly old, I suggest that you ***try Ubuntu 10.04 LTS first***. It will be updated until April 2013.

Then I suggest that you try the current version 12.04, either ***Lubuntu*** with the ultra-light LXDE or ***Xubuntu*** with the light desktop environment XFCE.

This assumes that you have a broadband internet connection, otherwise you should focus and download only one iso file for a currently supported system to install.

It is possible to use your old Ubuntu 9.04 to download and make a boot drive, but it might be easier to use a computer with a an installed operating system for that purpose.

3. Try your Ubuntu install CD drive(s) as live systems. Do not install anything at first, only test the look and feel of the system(s).

You might need some ***boot option*** to get [LX]Ubuntu working properly. See [[COLOR="red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

4. And after these steps, and some discussions, I think you will be ready to install your version and flavour of Ubuntu to the hard disk drive.

---

### Post by daisydew on 2012-07-17
I have slow dial up on this PC.  I would have to have a new up grade disk for my Dell.
I cannot make a new boot disk. If I go into dos, I get a few lines going so fast I cant read, then ubuntu starts up.  Dos will not start up for me to change anything.  ubuntu will not let me change anything. I have no internet hookup with ubuntu on this machine. I get an error message if I try anything. I cannot access the wireless.  No matter if I try to load any software disk, ubuntu won't let me. No disk will boot on dos.  I have tried almost every thing my limited knowledge of computers understands.  I have even tried to use a wipe out disk, but dos always reboots to ubuntu.  If you think an upgrade will help, I need a disk.

---

### Post by sudodus on 2012-07-18
> **daisydew said:**
> I have a Dell Inspiron 1501 that had Vista installed. Didn't want it so installed Ubuntu9.04 disk.  It wiped out Vista and now I cannot open anything. I always get a archive error. No wireless. Cannot reinstall Vista.  Cannot uninstall Ubuntu. Cannot reinstall ubuntu. Cannot wipe hard drive and start over.  Dos  boot will not work.  Goes back to Ubuntu. Ran problem report.
...
Computer now in worthless state.  What can I do?

> **daisydew said:**
> I have slow dial up on this PC.  I would have to have a new up grade disk for my Dell.
I cannot make a new boot disk. If I go into dos, I get a few lines going so fast I cant read, then ubuntu starts up.  Dos will not start up for me to change anything.  ubuntu will not let me change anything. I have no internet hookup with ubuntu on this machine. I get an error message if I try anything. I cannot access the wireless.  No matter if I try to load any software disk, ubuntu won't let me. No disk will boot on dos.  I have tried almost every thing my limited knowledge of computers understands.  I have even tried to use a wipe out disk, but dos always reboots to ubuntu.  If you think an upgrade will help, I need a disk.

I think what you call DOS is actually the 'grub menu' and/or 'busybox'. 

Grub is the boot-loader, and its menu can offer possibilities to boot several operating systems or debugging programs from a text window. > BusyBox combines tiny versions of many common UNIX utilities into a single small executable.

-o-

I'm not sure
1. if you have a regular Ubuntu install CD, that can be used to run a live session 'Try Ubuntu without installing it',
2. or if it is an alternate CD, that can only install (but is better when there are certain problems or limits with the hardware).

But I think it is (1.) and that you can boot a live session 'Try Ubuntu without installing it'. This way you can actually run your computer and do a lot of things, including installing Ubuntu, but also a lot of other things. I suggest that you try it :-) and learn the basics how to use Ubuntu.

You probably need some boot option to get Ubuntu working properly. If necessary, see the following link from another computer and make notes to use on this Dell Inspiron. [[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

It it possible for you to connect via an ethernet cable to a local area network or to the internet?

As I wrote in post #2, Ubuntu 9.04 has passed end-of-life, but I suggest you use it to get something running, and later on decide what to download (and where to download it). Probably some friend, relative or colleague with broadband connection to the internet can help you to download a current version of Lubuntu, Xubuntu or 'vanilla' Ubuntu.

---


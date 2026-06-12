---
title: "PXE boot install Windows XP from Ubuntu issue"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xe2bss on 2009-06-12
I do have a Dell Latitude C400 with no CDROM drive and no OS, I need to load Windows XP on it, so I decided to try PXE boot using another laptop running Ubuntu 8.10.

So far I have the dhcp server running fine: 

ddns-update-style none;
default-lease-time 86400;
max-lease-time 604800;
option domain-name-servers 172.16.1.1;
authoritative;
#
#
subnet 172.16.1.0 netmask 255.255.255.0 {
         range 172.16.1.10 172.16.1.254;
         filename "/tftpboot/winxp/i386/startrom.n12";
         next-server 172.16.1.1;
         option subnet-mask 255.255.255.0;ddns-update-style none;
default-lease-time 86400;
max-lease-time 604800;
option domain-name-servers 172.16.1.1;
authoritative;
#
#
subnet 172.16.1.0 netmask 255.255.255.0 {
         range 172.16.1.10 172.16.1.254;
         filename "/tftpboot/winxp/i386/startrom.n12";
         next-server 172.16.1.1;
         option subnet-mask 255.255.255.0;
         option routers 172.16.1.1;
         }
#

I choose onboard NIC boot in the C400 and it grabs an IP ok, no problem so the DHCP part of the whole PXE boot process is ok. I created a folder in the Ubuntu laptop called /tftpboot/winxp/i386 and  copied all the contents of the i386 folder of an Windows XP install CD into it, I have followed several recommendations on how to do this part but so far no luck, I have got as far as getting the 
"setup is checking your computer" message from the beggining of the install process but it halts right there. Does someone has a step by step on what files the dhcpd server must pass to the host and what other files have to e available and in what order?

Thanks
XE2BSS

---

### Post by sugi007 on 2009-06-15
I have also been looking at the same thing except my server is a windows computer, Sorry! [-( . 

Anyway I think you may get a good idea of the general process from my blog post [here]("http://www.codesingh.com/2009/06/walkthrough-install-win-xp-by-booting.html"). It is quite in depth and has screen shots of each stage. 

Hope it helps

---

### Post by jaqrah on 2009-06-16
I know this is besides the point but...

Do you know you can install xp using a usb stick?  I installed xp pro on my dell mini 9 this way.  If you are interested I will find the information and directions on how to do it.

---

### Post by wentzr on 2009-08-14
> **jaqrah said:**
> I know this is besides the point but...

Do you know you can install xp using a usb stick?  I installed xp pro on my dell mini 9 this way.  If you are interested I will find the information and directions on how to do it.


It would be great if you could find that info and post back. Definitely would be more useful than basically saying "i know how to do this, let me know if you to know too"... what use is that to anyone?? :) 

I've dug and haven't come up with a solution that *works*  my laptop has a busted CD/DVD drive and using a usb external cd/dvd drive (have tried several enclosures, several DVD/CD drives) does not work.. my bios does not pick up the CD rom under the USB guise.. 

How do you create an XP boot installer on a USB stick? I've made an iso out of my (perfectly legit) XP installer CD, but Ubuntu's "USB Startup Disk creator" claims the iso is not a "desktop install".. what gives.. also have formatted the usb disk (1 gig) on a mac as a windows bootable volume (in disk utility on os x, then copied the contents of the XP installer onto the win-boot formatted usb disk in ubuntu... when booting off this usb stick on the target system, i just get "boot error" .. any light you could shed, jaqrah, would be appreciated by me and maybe some others in the community. I'm looking into doing a network PXE boot in the meantime. . . 

Thanks!

---

### Post by jaqrah on 2009-08-14
[http://www.boot-land.net/forums/index.php?showtopic=4900](http://www.boot-land.net/forums/index.php?showtopic=4900)

This link should do the trick.  

The first time I did this I just had the USB_Multiboot folder and kind of intuitively made my way through all of it.  I didn't even know that there was this user forum (will be bookmarking).

It definitely works for XP.  I have loaded 2 different version of XP on each of my mini9s at various points.

Hope this is enough for everyone!:)

---

### Post by wentzr on 2009-08-15
> **jaqrah said:**
> [http://www.boot-land.net/forums/index.php?showtopic=4900](http://www.boot-land.net/forums/index.php?showtopic=4900)

This link should do the trick.  

The first time I did this I just had the USB_Multiboot folder and kind of intuitively made my way through all of it.  I didn't even know that there was this user forum (will be bookmarking).

It definitely works for XP.  I have loaded 2 different version of XP on each of my mini9s at various points.

Hope this is enough for everyone!:)

nice. that was pretty much an immediate reply!! I appreciate it.. diggin in now.

---


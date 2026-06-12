---
title: "Timer twice as fast than reality"
date: 2006-01-18
forum: General Help
---

### Post by rivasdiaz on 2006-01-18
Hello

I have installed ubuntu breezy. Everything is working fine, except for a few details.

The biggest problem that I have is that my ubuntu system is reporting the time twice as fast than reality.

I checked the forums and mail, and found a similar error for a previous ubuntu and the recomendation of adding no_timer_check in my /boot/brub/menu.lst

I added this line but my system is still reporting the time twice as fast as reality.

What else can I try?

Thanks in advace for any help.

Hardware:

Laptop Acer Ferrari 4000
Microprocessor: AMD Turion64 Mobile
Video: ATI Mobility Radeon X700 (128MB)
RAM: 1GB

Software:

OS: Ubuntu 5.10 (Breezy)
Kernel:  2.6.12-10.25 (386)
Video: ATI Propietary Driver 8.20.8

The entry that I'm selecting on the grub menu to boot says in menu.lst:

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro no_timer_check quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

---

### Post by jumpslu7 on 2006-01-18
I came across a similar problem when I first installed a linux with a 2.6 kernel as a VMWare virtual machine.  It seems that its a less than trivial kernel bug that won't be fixed any time soon.

A simple remedy is to add the following line to root's crontab:

0-59/1 * * * * /usr/sbin/ntpdate -u 194.168.4.76 > /dev/null 2>&1

this synchs the system time with the ntp service on 194.168.4.76 (ntl isp in the uk) once every minute.  

I ain't holding my breath for the kernel fix(!)  Incidentally I've never encountered this problem on an install to a dedicated system, which is why the kernel bug doesn't seem to be much of a priority to the linux developers.

The fix I've suggested above is a dirty hack like, and if you need more precise time, well, sorry, I'm out of ideas, but I hope this helps some!

If you do go with my solution above, it's best to find a ntp service on your own ISP's network, in order to ensure as accurate a time update as possible.

hope this helps 
j

---

### Post by rivasdiaz on 2006-01-18
[QUOTE=jumpslu7]I came across a similar problem when I first installed a linux with a 2.6 kernel as a VMWare virtual machine.  It seems that its a less than trivial kernel bug that won't be fixed any time soon.

A simple remedy is to add the following line to root's crontab:

0-59/1 * * * * /usr/sbin/ntpdate -u 194.168.4.76 > /dev/null 2>&1

this synchs the system time with the ntp service on 194.168.4.76 (ntl isp in the uk) once every minute.  

I ain't holding my breath for the kernel fix(!)  Incidentally I've never encountered this problem on an install to a dedicated system, which is why the kernel bug doesn't seem to be much of a priority to the linux developers.

The fix I've suggested above is a dirty hack like, and if you need more precise time, well, sorry, I'm out of ideas, but I hope this helps some!

If you do go with my solution above, it's best to find a ntp service on your own ISP's network, in order to ensure as accurate a time update as possible.

hope this helps 
j[/QUOTE]
Well the problem is that most of the time I'm behind a firewall wich only allows http so no ntp is allowed.

---

### Post by David Valentine on 2006-01-19
Sounds like the double clock speed bug--I had much the same thing, plus when I tried to play music files, they played twice as fast as they should have!:eek: 

The howto for dealing with it is at [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)

For my system (ubuntu 32 bit on a 64-bit AMD Sempron), the noapictimer irqpoll fix worked.  Your mileage may vary.

---


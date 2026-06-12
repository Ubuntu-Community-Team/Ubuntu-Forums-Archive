---
title: "Live CD fails bootup at Xserver"
date: 2006-02-11
forum: Desktop Environments
---

### Post by R_MAC on 2006-02-11
I downloaded the latest Breezy Badger Live CD boot image, and burned it to CD/ISO. 

Live CD boots, goes thru all the screens, incl. graphic 
logo, hardware detection, etc, gets to a blue screen that says "Failed to start X server gui..." etc. and dumps me at a "ubuntu:~$" prompt. If I enter "startx" or "sudo startx"
(my limit at Unix commands) it cycles thru messages about the X server failing
etc and returns to prompt. What now???

As per other threads here, tried "sudo dpkg-reconfigure xserver-xorg" 
and took all defaults except graphics card=VESA, replied with 
"Dummy template for processing unavailable question [false---]... 
if you see this template, you have found a bug- file a report". 

Then entered: "sudo startx", 
Msgs returned:
"creating new auth file, 
creating new /home/ubuntu/.serverauth .18763, 
creating new /home/ubuntu/.xauthority (2 times), 
giving up, 
xinit:connection failed (errorno 111), 
xinit: no such process (errorno 3),
server error,
-$ prompt again
HELP!!!

Someone suggested I "look in /var/log/Xorg.0.log (or /var/log/xorg.0.log) to see exactly what is the problem" ?? 
There is no file by that name in /var/log/ (??) 
(Please forgive, I am a newbie and know little of Linux commands)

Gateway "Essential" Desktop
Intel Pentium III- 450mHz
W98se
256mb ram
nVidia GeForce2 MX/MX400
Sony CPD-100ES 15" monitor
IBM 10gb IDE pri
Seagate 10gb IDE slave
SoundBlaster 128
Network Everywhere ethernet 10/100 card/cat5e 
Linksys DSL  router-firewall-10/100 swt

---

### Post by R_MAC on 2006-02-12
SUCCESS!!-- CD boot image was made on CDRW on 1 drive & booted on another.  Once booted from original burner drive, all worked like a charm- went right to desktop and I'm using it now to reply to this thread. Mouse is very ssslllooowww but workslThanks for all who tried to help.

---


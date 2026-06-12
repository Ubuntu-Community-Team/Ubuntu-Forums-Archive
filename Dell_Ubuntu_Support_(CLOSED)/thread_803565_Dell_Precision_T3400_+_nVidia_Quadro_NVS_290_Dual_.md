---
title: "Dell Precision T3400 + nVidia Quadro NVS 290 Dual Head"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Christofurriebum on 2008-05-22
Hi All,

I've recently convinced my employer to purchase a Dell Precision T3400 WorkStation with a nVidia Quadro NVS 290 Dual Head graphics card.

The reason I chose this system was because it was Linux "tested", but I have been experiencing problems.

Should I be using the Ubuntu 64bit version?

I tried using Hardy 8.04 (i386) and it would not boot reliably - specifically, my system would hang during the install (on the way back up on its initial boot, after the CD had been ejected).  When I tried again, the system refused to boot onto the CD at all!

I tried using the Gutsy CD (i386) to install and again, I experienced unreliability issues, but this time they were related to getting and retaining a DHCP lease.  The system allowed me (as either 'admin' or 'oem' users), to install the updates that it detected were available and my networking was fine, but upon completing the install and rebooting, I was left in a very odd state.

I could see that the onboard NIC had no IP.  However, if I changed into a command prompt, I could log in and use 'ifconfig' to see that there was no IP, then 'dhclient' and watched it request, then receive a valid IP, but that the IP was not in place on the NIC afterwards.  This I found very confusing.

I have temporarily moved over to CentOS but really want to give Ubuntu another chance, as it's much friendlier to use.

Please can anyone help me identify the problem(s) and get up and running Ubuntu?

I intend on configuring Xinerama Dual Head capability in Xorg as soon as I have a stable system.  I have a Dell PE800 at home, running Ubuntu Gutsy and driving 3 monitors with a PNY nVidia Quadro NVS 440 graphics card, so am hopeful that I can do this...

---

### Post by pzs on 2008-07-24
Did you make any progress with this? I'm considering a similar configuration.

---

### Post by Christofurriebum on 2008-07-24
Not with Ubuntu.

I've chosen CentOS which is very usable.

See this link for the help I received in the [Dell forum]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=13906")

Cheers!

---

### Post by zaffar.unixed on 2009-01-28
Hi  Friend ,

you have to restart the system and go to the bios mode , 
 
for that press F12 
it will prompt u  to setup mode 
go onborad device { if u want to install via disk }
if u want to install via network 
go to integrated nic [press enter ]
activate clicking on "onw/pxe "
save it and exit . 

then it will automatically install the os

---

### Post by pgilmon on 2009-05-06
I am having issues installing 9.04 on a Dell precision T4300 with two NVS 290. The live-CD won't start in graphics mode.

---

### Post by pgilmon on 2009-05-06
I have finally make it work. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1142173").

---

### Post by Christofurriebum on 2009-09-13
I found a similarly weird problem when my company forced me to switch to Windows XP.

The system would not boot unless the install CD was in the drive...

I found the solution to this sort of accidentally while looking around the BIOS.  Yes, I had not set my hard drive in the boot options menu - berk!

---

### Post by blacklight332 on 2009-11-13
I had the same problem on my dell t3400 workstation with nvidia quadro nvs 290.  Ubuntu 9.10 live CD (karmic) would freeze during xsplash (the ubuntu brown spotlight)... i solved it by adding xforcevesa to the live cd boot options.  This is fine to use the vesa graphics driver for install because once you get it install you will be using the nvidia driver over the long term anyway.

---


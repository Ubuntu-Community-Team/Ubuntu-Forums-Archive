---
title: "I can't start Live CD"
date: 2007-05-05
forum: Desktop Environments
---

### Post by _Seven_ on 2007-05-05
Hi guys! Well i put the cd of Ubuntu 7.04 but before starting the Live CD appear an error about Xorg because have incompatibilities with my graphic card (ATI Mobility Radeon X1450), saying that:
"
X Window System Version: 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System : Linux ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 15 07:36:31
Build Date: 04 April 2007
    Before reporting problem check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the lastest version
Module Load present
Markers: (--) probed, (**) from config file, (==) default setting,(++) from command line,(!!) notice,(II) informational, (WW) warning, (EE) error,
            (NI) not implemented, (??) unkown
(==) Log file: "/var/log/Xorg.0.log", Time Sat Apr 28 10:54:41 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) VESA(0): No matching modes
(EE) Sceen(s) found but none have a usable configuration

Fatal Server error:
     no screens found.
"

Then a message appear saying that:"X server is now disabled. Restart GDM when it is configurd correctly" 
And finally Ubuntu starts in command line! Apparently all files are avaiable, i do the command "ls" on Desktop folder and appear:
"Examples  ubiquity-gtkui.desktop"
i do the command "ls" in cdrom folder and appear all files including the file "install".

There's a way to solve the situacion of Xorg? I read somehere about chipset SIS on motherboards and this chipsets have problems with VESA but i don't know if it is true or if it is, how to change it on Live CD. But unfortnely if we can't solve the Xorg problem and start the Live CD it is possible to install Ubuntu 7.04 in command line?

I have a laptop Asus A7CC, Dual Core 2GHz, 2GB Ram and a hard drive of 160 GB.

Thanks very mouch i really need your help.
Be good.

---

### Post by AtrejuT on 2007-05-05
the easiest solution (if you indeed want to install ubuntu and not just try out the livecd) will be to use the alternate install cd instead. that should work without these problems and is available at [www.ubuntu.com](www.ubuntu.com) as well (check the box about the alternate cd on the bottom of the download page)

---

### Post by WSayin on 2007-05-05
I have the exact same problem, so thanks for the help!

---

### Post by jbmech006 on 2007-05-06
Hi Guys, 

I've been hunting on the web all day for a fix to this problem. It seems that a lot of people are having this problem. I have a ATI Mobility X1400 and I have the same Fatal server error: no screens found. I am going to try out the alternate installer because so far it doesn't look like anyone has a solution to this problem. A lot of people have suggested modifying the xorg.conf file with different parameters and so far nothing has worked. I'll let you guys know if the alternate install has the same problem. 

Regards

---

### Post by Joe325 on 2007-05-07
HI,

This is my first post to anything but since I started using Ubuntu a few months back on my desktop, Im loving it. Anyway, Iwanted to try it on my laptop.
I insert the CD to try a live run of it to make sure all my laptop hardware works. Once the ubuntu splash screen disappears, I hear the ubuntu theme sounds but my laptop doesnt display the screen.
Ive tried with 6.06 and 6.10 but both 'stop responding' at the same point. Ive left it on to see if it was just a delay but nothing happened. Even to eject the CD, I had to hold the power button to turn off and remove CD on next reboot.
My laptop is a Excel D410J which uses Unichrome Pro/VIA chipset graphics card, Sempron 2600 CPU, 1Gb RAM, K8N800 board. 
Any help is appreciated....

---

### Post by whalefreezer on 2007-05-13
I'm having the same problem too.

Any help would be appreciated:)

---

### Post by RedSquirrel on 2007-05-13
This is a sticky at the top of Absolute Beginner Talk:

[URL="http://ubuntuforums.org/showthread.php?t=414194"]Installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards
[/URL]
Good luck.

---

### Post by Joe325 on 2007-05-13
HI,

I downloaded 7.04 and am getting same error as 6.06 & 6.10. I found 5.10 version and was able to run Live CD to check all hardware compatability. Any reason why the latest releases dont work on my laptop ???

---

### Post by helliewm on 2007-05-14
Dapper will install, I then upgraded to Edgy and then Feisty to ensure I was connected to the internet. I then typed in the commands exactly as in the Sticky mentioned above.  I even ended up with Beryl working! This will solve your problem ,its time consuming though.

Helen

---


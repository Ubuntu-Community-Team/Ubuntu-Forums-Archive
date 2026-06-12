---
title: "Dell Dimension 2400 Video problem in 8.10"
date: 2008-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wiley692 on 2008-11-03
I just installed 8.10 from 8.04 and I cannot see anything on the screen. The computer is a Dell Dimension 2400 with a P4 processor and an Intel 82845G/GL/GE/PE/GV Graphics controller. The live CD and the alternate install CD both did the same thing. It is fine until it passes the logon screen then it goes black and the only thing on the screen is the mouse arrow which moves so it isn't locked. I never had this problem with 8.04. I can't fix anything if I can't see it. I am NOT an experienced linux user. I am good with windows but don't do anything with linux except turn it on and use it some so if the fix is going to be really complicated I will probably just go back to 8.04. Hope someone can help!

---

### Post by wiley692 on 2008-11-03
I have tried quite a few more times and sometimes the screen is the ubuntu beige also. Otherwise the exact same problem.

---

### Post by Marikawn on 2008-11-03
I had the same problem. I also have a Dell Dimension 2400 with Ubuntu 8.10 installed. What I did was install it from the CD and at the initial menu I hit the f4 option and selected safe graphics mode then installed Ubuntu like that. My problem now is that it is not detecting the onboard video card and is defaulting to one called 'vesa' which only lets me see in 640 x 480. Let me know if you have any updates.

Maybe try to reinstall Ubuntu from the CD from scratch again. If not go to Ctrl + f1, I believe and view the file type: sudo nano /etc/X11/xorg.conf  , which is where the information of your video card is. In that file is listed a command that you can execute to reconfigure that information, who knows if you run that command you may be able to fix your problem. If not read off what it says.

Mine says:

> 
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection



---

### Post by wiley692 on 2008-11-04
I wanted to uninstall ubuntu and go back to the older version but it would not let me boot from any bootable cd that I have used in the past to get rid of it. I finally had to use an old DOS boot disk and fdisk to get rid of it so I could restore my windows backup. Did anyone even bother testing this on a Dell? It seems like a lot of people are having dell problems with it that they didn't have with the previous version.

---

### Post by juangiovanni on 2008-11-06
I had the same problem, but followed the steps in this post to fix it.  [http://ubuntuforums.org/showthread.php?t=965022](http://ubuntuforums.org/showthread.php?t=965022) 

It's a problem with compix.
JG

[COLOR="Blue"]Here's a quote from the author:

 Originally Posted by jerrylamos  View Post
Any number of us are having problems with 8.10 compiz. My thinkpad gets a black or tan screen instead of a desktop. The workaround in Launchpad Bug #259385 is:

boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If later on you want to try compiz you can install it with Synaptic. As of today compiz still freezes my pc. The "official" fix is blacklisting some graphics hardware so that compiz won't start.

Jerry[/COLOR]

---


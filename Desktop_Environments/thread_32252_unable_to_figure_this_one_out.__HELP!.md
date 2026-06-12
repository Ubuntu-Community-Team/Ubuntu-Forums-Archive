---
title: "unable to figure this one out.  HELP!"
date: 2005-05-06
forum: Desktop Environments
---

### Post by Borrowed Lab Monkey on 2005-05-06
](*,)
I wrote about this problem several days ago and got some excellant feedback.  Problem is that i just cant get my unstable video size to correct itself.  The screen randomly narrows about an inch (half an inch on either side) then reinflates itelf back to full size; never changing resolution while its doing that.  Its very hard to get anything acomplished when i have to get up and walk away from the thing every 10 minutes.  Ive sifted through the error log after error log and the only thing i found was relating to my IDE raid card. (no surprise, as nothing seems to support it, but i digress...)  So basicly, im new to this, and i need the guys who walk softly and carry big keyboards to help me out, starting from the smalles things that i might over look and up.  Thanks in advance for the help.

My Hardware config is as follows...
AMD Athlon XP 1800+
Gigabyte GA-7ZXE Motherboard (no onboard video)
786MB PC133 Ram
Saphire ATI 7500 w/128Mb DDR
SB Live 5.1 Platinum
3com 10/100 Nic
Avermedia PCI350 TV tuner card
SIL 640 IDE/PCI RAID 0+1 adapter
Benq 8x4x16 dvd+/- dual layer burner (connected to mobo ide)
Aopen 16x dvd Rom (connected to mobo ide)
Western Digital wdd200 (connected to mobo ide)
Western digital wdd400 (connected to PCI controllerin raid 0+1 array with samsung)
Samsung 40 gig (connected to PCI controller in Raid 0+1 array with WDD400)
and a patridge in a pear tree  ;-)

---

### Post by Psquared on 2005-05-06
I suspect its the Partridge or the Pear Tree. ;)

Do you have the most current ATI drivers?

Have you tried adjusting your settings with xvidtune?

---

### Post by crazybill on 2005-05-07
Assuming that your video card has worked with Windows or whatever system you used with this hardware before... so that you know your card is OK, it sounds like  you need an updated video driver... else try another video card.

I have installed ubuntu/kubuntu on quite a few computers now w/different hardware and on a couple, I never could get the video card to work right so I just switched it out... if you have that luxury.

Try looking for an updated driver first.

---

### Post by crazybill on 2005-05-07
Just an after thought.

Before you do any major reconfiguration, have you tried this:

***sudo dpkg-reconfigure xserver-xorg && sudo reboot***

You might also checkout this website:

[http://www.tldp.org/HOWTO/Hardware-HOWTO/](http://www.tldp.org/HOWTO/Hardware-HOWTO/)

---


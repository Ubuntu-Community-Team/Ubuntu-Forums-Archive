---
title: "POST &amp; BIOS load times regarding USB boot"
date: 2010-09-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mr Tickle on 2010-09-22
Hi Ubuntu forum members, just wondering if any of you could help me. (I have had a quick check around on this forum but couldn't find any relevant thread regarding the issue I have)

Recently I got this brand new laptop from dell - Studio 1558 - Core I5 M 450 - 4GB RAM - 640GB HDD, etc.
It has Windows 7 64 bit Premium edition already loaded as the default OS. 

I have Ubuntu 10.04 Lucid Lynx on a 1TB Western digital my passport essentials SE portable hard drive. This allows me to take it to most computers and boot from there - don't need to haul my laptop around. 

--- PROBLEM ---

I set my studio laptop's BIOS to USB boot device as the first in line when loading an OS. However what happens is that it goes through it's POST at such a rate that it fails to pick up my portable HDD (WD passport) and boots straight up into windows 7. My current solution is that when the Dell POST/BIOS screen appears I go into BIOS setup (Pressing F2) and then simply exit the BIOS, this then restarts the laptop's BIOS (I believe form what I have seen) - but leaves the power on (Thus keeping the passport powered on and connected) and this gives the computer enough time to locate the WD Portable HDD and boot from there. Everything loads fine from that point on and Ubuntu runs smoothly :)

--- PROBLEM ---

Now is there any remedy to my problem. I have already tweaked the BIOS to the extent that:
a) USB boot is second from bottom - Above the Internal HDD (Just            to give that extra bit of time if possible)
b) Turned off the Fast BIOS boot sequence, and enabled the connected hardware display (Shows details of components of the laptop). Again trying to make the laptop slower (can you believe...) in its POST/BIOS to at least recognise the WD portable HDD, again to no success :(

I tried calling the Dell support line (I'm in the UK) but they told me to go into Windows 7's BOOT.INI file and edit that to make it boot from the PHDD first instead - Didn't explain how though.

So is editing the BOOT.INI file the way to go and if so how would I go about doing that without causing any major damage, I.E windows 7 not booting. (I do have a disk image backup though - Praise Acronis true Image)    

It's not a serious issue but it would be nice not having to enter setup every time I wish to run Ubuntu = 90%+ of the time.    

Also on another note I found that Ubuntu  9.04 (Karmic Koala I believe) loaded up 10 - 15 seconds (Through the WD portable HDD) quicker on my old laptop than Windows 7 does on this one (Windows 7 was fresh - no added software) That is quite crazy!

Old Laptop - 32 bit(Dell inspiron 6000): 1.4GHZ Celeron (Single core) 2GB RAM 

New Laptop - 64 bit(Studio 1558 ): Specs as above


Thanks for any responses - Mr Tickle :P

---

### Post by Mr Tickle on 2010-09-25
(Bump) Anyone any hints?

---

### Post by Sylslay on 2010-09-25
Intresting, but I had no remedy too.
I think that windos XP and above aren't easy for tweak files like. config.sys, boot.ini and autoexec.bat, that was easy with win95 and 98.

BTW about Yours new laptop. Laptop is new, but is any newer BIOS for it on 
dell suport web. Give it try:

[http://support.euro.dell.com/support/downloads/driverslist.aspx?c=ie&cs=iedhs1&l=en&s=dhs&ServiceTag=&SystemID=STUDIO1558&os=W764&osl=en&catid=&impid=](http://support.euro.dell.com/support/downloads/driverslist.aspx?c=ie&cs=iedhs1&l=en&s=dhs&ServiceTag=&SystemID=STUDIO1558&os=W764&osl=en&catid=&impid=)

Latest version of Bios is from 14-09-2010 and is A10 for Dell Studio 1558

---

### Post by Mr Tickle on 2010-09-25
Thanks Sylslay for the BIOS tip - I'll give that a shot.

Thanks again :)

---


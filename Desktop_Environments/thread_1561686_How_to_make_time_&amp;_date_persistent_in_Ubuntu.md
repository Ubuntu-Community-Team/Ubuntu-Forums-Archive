---
title: "How to make time &amp; date persistent in Ubuntu"
date: 2010-08-26
forum: Desktop Environments
---

### Post by benny7440 on 2010-08-26
I've noticed that every time this desktop is turned on the date & time are as they were the last time I used it, and then have to put in the correct date & time again (this is why I chose the word 'persistent' within the tittle). When I try to change those have to write in the password for the date as well as for the time as if 'login-in' once were not enough!
   What I want to know is how to put in the date & time and receive the correct amounts the next time I turn the unit on again, as it should be? Do I've to open a terminal & do it with administrator's authority/credentials?
   Thanks in advanced for any help on this!

---

### Post by Eksra on 2010-08-26
using an NTP (Network Time Protocol) would be the best way, because it's more accurate (usually) than your system clock in your bios (not sure why your ubuntu clock would not be grabbing the date/time from your bios.... is your Li battery dying?)

I use ntp.usno.navy.mil (they use the Atomic Clock, they need very precise time for naval navigation, and my father works for them, so that's why I picked them ;-) but there are many NTPs)

---

### Post by 3Miro on 2010-08-26
Do you dual-boot with Vista? There are some differences with the way Vista and Ubuntu work with time and this causes problems sometimes.

If not, then it sounds like a hardware issue, maybe the clock battery on the motherboard is loose or low on power. 

You should probably set it up so that Ubuntu detects the time automatically form the Internet. Check this one:

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

BTW: the fact that you are required a password to change the system time is an important security issue, some systems will go as far as requiring a reboot every time you change the system time. A request for password is a good middle ground.

---

### Post by Eksra on 2010-08-26
> **3Miro said:**
> maybe the clock battery on the motherboard is loose or low on power. 

You should probably set it up so that Ubuntu detects the time automatically form the Internet. Check this one:

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

As far as I know there is only ever 1 Li battery on the motherboard, and that's for the CMOS which powers the BIOS ramdac (and subsequently clock), so yeah, low battery.

And thats a good link for NTP setup - I still vote to go with the ntp.usno.navy.mil as they use the atomic clock and are updated themselves every 5 minutes or so.

---


---
title: "Problems with 8.04 (WiFi, open VPN, random system lockups,	CMOS corruption)"
date: 2008-05-17
forum: Desktop Environments
---

### Post by esj on 2008-05-17
summary of problems:

Laptop:

  o WiFi (Intel  3945ABG) not recognized, solution involves back port modules and wicd.

  o WiFi solution lost my open VPN management capability.

wife's desktop:

  o migration from 7.10 to 8.04 caused random lockups with associated CMOS corruption

  o Firefox three plug-ins are not exactly functioning right.

detailed chatter:

On my lap top, everything seemed to work okay except for WiFi.  WiFi is an Intel chip, 3945ABG.  After following instructions found elsewhere on the net which involved installing back port modules and replacing net manager with wicd, I finally got WiFi working.  Unfortunately, I lost open VPN management.  The only other management tool I found was KVpnc which, is from my experience, quite user hostile.  For example, when importing an openvpn configuration, it expects passwords for IP sec.  I can mostly live with the quirks of 8.04 on my laptop except for the open VPN problem.  I need that functionality back for work.


On my wife's desktop, the first problem noticed was that Firefox 3 had numerous  problems with plug-ins like flash and Java.  Given that she's addicted to things like youtube, Pop cap, cheeseburger and the like, this is a serious problem.  Solution was to downgrade Firefox to version 2. The second and more serious problem is that her machine locks up at random and sometimes won't reboot unless you power off.  Frequently the CMOS is corrupted.  Like many of you, my first thought was the CMOS battery is gone.  Replaced it, no change.  A second thought was thermal overload but again, with additional cooling from an external fan, no change.  The only difference was upgrading to 8.04.  Which leads me to the  conclusion that something in 8.04 is locking up and corrupting CMOS.  I've also tried turning off apic but again, no difference.

If you folks, who are much smarter than I am, can't help me with a solution, its time to downgrade to 7.10 and give up 8.04 as a lost cause.  I really want to stay with 8.04 if for no other reason than it's a lot less work for me than downgrading would be.

help would really be appreciated.

---

### Post by esj on 2008-05-19
> **esj said:**
> 
On my wife's desktop, the first problem noticed was that Firefox 3 had numerous  problems with plug-ins like flash and Java.  Given that she's addicted to things like youtube, Pop cap, cheeseburger and the like, this is a serious problem.  Solution was to downgrade Firefox to version 2. The second and more serious problem is that her machine locks up at random and sometimes won't reboot unless you power off.  Frequently the CMOS is corrupted.  Like many of you, my first thought was the CMOS battery is gone.  Replaced it, no change.  A second thought was thermal overload but again, with additional cooling from an external fan, no change.  The only difference was upgrading to 8.04.  Which leads me to the  conclusion that something in 8.04 is locking up and corrupting CMOS.  I've also tried turning off apic but again, no difference.


Found a solution to this problem.  Turns out, it was a cooling problem but not one that could be helped by an external fan.  A friend of my suggested I check to make sure the thermal compound between heatsink and CPU chip was in good shape.  Sometimes it dries out, sometimes there's not enough but, the end result is the same.  I didn't believe him but, I was desperate so I popped off the heatsink and much to my surprise, there was a thin bead of thermal compound around the edge of the CPU chip and a couple spots in the middle.  I trotted down to my local RadioShack, spend $10 on a tiny little tube of magic goo with silver in it, applied said goo to CPU and heatsink and shazam, the system is stable.  Not only that, my wife reports that it is running faster and more reliably than before.

From as near as I can figure out, the original state actually insulated the CPU chip from the heatsink and that there was a difference between 7.10 and 8.04 in how the software ran which in turn changed how much heat was generated.  Very weird.  I guess the moral of the story is don't skimp on the magic goo.

---


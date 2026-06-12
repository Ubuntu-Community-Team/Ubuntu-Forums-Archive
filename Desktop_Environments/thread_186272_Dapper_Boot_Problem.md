---
title: "Dapper Boot Problem"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Protege on 2006-06-01
Okay so I have searched this forum and Google but I am unable to find an answer to my problem. I have a intel SDS2 server board with dual pentium 3's and a gig of pc133. I installed 5.10 with no problems and I want to upgrade to dapper. So to make sure I could run dapper with no problems I decided to boot from the Dapper  Live cd and after choosing to start/install dapper on the boot menu I get a 

[4294669.627000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC

this happens after uncompressing the kernal.

Any thoughts?

---

### Post by Protege on 2006-06-01
NVM I gotta learn to refine my search technique. :) Found a solution here.

[http://ubuntuforums.org/showthread.php?t=174634&highlight=MP-BIOS+bug](http://ubuntuforums.org/showthread.php?t=174634&highlight=MP-BIOS+bug)

---

### Post by Protege on 2006-06-05
Well that previous solution got me to the boot screen but while loading it seems to stall on Loading Hardware Drivers and pressing crtl+c will not skip it. This is when I try to boot from the live cd. I also tried to upgrade from the Terminal and when the install gets to starting PCMCIA devices it locks up. If I install from the Update Manager it all goes fine until I reboot at which time I get the BIOS bug from above then once I edit the boot line to get passt that the loading hardware drivers hangs again... Anyone got any ideas? I love Ubuntu and I really want dapper to work on this computer.

---

### Post by Protege on 2006-06-05
bump..

---

### Post by Protege on 2006-06-05
117 views of this thread and no one can even say "me too" or "I've heard of this before..." I don't want to come of as rude or sarcastic, but come on people nobody has anything to say?

---

### Post by marsman8790 on 2006-09-14
I have the same issue upon boot however once it does boot using the noapic option it just hangs at initilizing system services and i have no idea how to make it just boot normally - i really am at a loss as i really dislike windows

---


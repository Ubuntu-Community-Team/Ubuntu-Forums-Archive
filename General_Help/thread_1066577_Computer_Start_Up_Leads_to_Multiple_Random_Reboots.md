---
title: "Computer Start Up Leads to Multiple Random Reboots"
date: 2009-02-11
forum: General Help
---

### Post by odduck on 2009-02-11
Here's my problem scenario: When I go to start up my computer after turning it off for the night, it will boot up fine at first, then I'll start using a program (doesn't seem to matter which one), and then the computer will just stop and start to reboot for no apparent reason.  Then it can sometimes take up to a dozen attempts at rebooting itself before it finally stays on, with the reboots all occurring at different points during the boot-up process.

I'm using Hardy Herron 8.04 on an HP Pavilion a430n.  I'd be happy to provide any sort of system log information needed if you can tell me how to get it :P

So far this problem is just a bit of a nuisance but I'm just afraid that it could end up being something more serious and would like to figure out what it is before my computer just decides not to load someday.

Thanks in advance.

---

### Post by Tamlynmac on 2009-02-11
Just a few question that migh help ID the problem. It does sound like it may be a hardware issue. Like you, I hate intermittent issue.

1. During the reboot does it get past the machine boot before it reboots? In other words does it reboot only when Ubuntu is loading or already up and running or does it reboot during the the machine language startup portion that displays you hardware, etc.? 

If any of the restarts occur during the machine boot then definitely continue below.

2. Do all the light flicker just prior to restart or any other unusual observance - possible power failure? 

3. Are all the fans running and can you confirm that that during the multiple restarts?

4. Have you checked to assure the reset button or power button aren't hanging and all I/O connections including the power plug are tight?

5. I've had a loose connector where my power supply plugs into my MB that caused a similar problem.

6. I would definitely check the wiring and connections in the box. Often a bad connections to the HD can also could create similar symptoms.

---

### Post by odduck on 2009-02-11
It definitely sometimes reboots during the machine boot up.  I haven't noticed any sort of external indicators (lights, plug, fans, etc) of anything unusual going on.  I'll have to check out the inside of the box sometime tomorrow as it's late here and post what I find then.

---

### Post by odduck on 2009-02-11
Ok, well I tried checking the connections inside the computer as best I could (I'm not a technician or anything) and I even cleaned it out pretty good (lots of dust and cat hair, the power sink needed a bit of work) but alas, it was for naught.  Booting up resulted in the same old dance as described above.  Any other suggestions for things to check?

---

### Post by Tamlynmac on 2009-02-11
No, I don't. I'd suggest you take it to a qualified tech.

---

### Post by odduck on 2009-02-11
Alright, thanks anyways.

---

### Post by fava on 2009-02-11
Sounds like a thermal issue to me, as the system warms up it becomes more stable.  If you boot off of a CD or flash drive and have the same problem then its most likely to be hardware/thermal related.

---

### Post by johnjohn2 on 2009-02-11
> **odduck said:**
> Ok, well I tried checking the connections inside the computer as best I could (I'm not a technician or anything) and I even cleaned it out pretty good (lots of dust and cat hair, the power sink needed a bit of work) but alas, it was for naught.  Booting up resulted in the same old dance as described above.  Any other suggestions for things to check?

Try booting to recovery (From Grub) and then selecting resume normal boot

---

### Post by odduck on 2009-02-12
> **fava said:**
> Sounds like a thermal issue to me, as the system warms up it becomes more stable.  If you boot off of a CD or flash drive and have the same problem then its most likely to be hardware/thermal related.

is there a way to maybe isolate and figure out what the problem component is?  my intuition says it's the power supply.

> **johnjohn2 said:**
> Try booting to recovery (From Grub) and then selecting resume normal boot

tried this and it seemed to be working for a while but then the computer rebooted itself after a few minutes.


i'm afraid that the problem seems to be getting worse so i might just have to take it in to have it looked at anyways.

---


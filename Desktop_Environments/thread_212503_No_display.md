---
title: "No display"
date: 2006-07-10
forum: Desktop Environments
---

### Post by samantha on 2006-07-10
Sir / Madam,

good day! I download Ubuntu 6.06 (i think its an Live CD)

now when i boot my system to CDROM drive the main menu on ubuntu will show. i select the first option (start or install ubuntu linux something) then after that it will begin to load systems files. after that my monitor will not display any thing but my Hardisk led light keeps lighting (activity) & my CDROM as well.

rig:
AMD Sempron 2800+
ASRock K8Upgrade
512MB DDR266
ATi Radeon 9550 128MB 128bit.

regards,

---

### Post by Dr. Nick on 2006-07-10
Have you tried the safe graphics mode yet? It may help if its video card related.

---

### Post by samantha on 2006-07-10
yes sir. same problem. i select the F4 & choose 800 X 600 with 16bit same problem.

i already install a previous version of ubuntu 5.x here @ my rig (not live cd).

please help.

---

### Post by Dr. Nick on 2006-07-10
any chance you could try a different monitor? I would guess its a video problem, does your hd/cd lights ever stop? So it appears its fully loaded and you just cant see it?

I havnt expierenced this before.

If you want 6.06 you can always backup important files and  upgrade you ver 5 over the network

---

### Post by samantha on 2006-07-10
i didn't test it with new monitor, but im sure its not them monitor cause a can use my XP on it.

hdd & CDROM are blinking indicate that i has an activity (installing or booting  blah....) only problem is i can't see it. my monitor light(power) is blinking (it should be steady light).

---

### Post by Dr. Nick on 2006-07-10
yeah, im sure your monitor still works, i was just thinking that maybe the live cd is setting a certain refresh rate that your monitor can not handle and thus causing the monitor to lose the video signal. A difffernet monito may support the settings it is chosing by default. 

I was curious if all cd/hdd lights stoped after a minute which would help determine if it finished loading, even if you couldnt see it.

---

### Post by samantha on 2006-07-10
yes sir, im thinking that it has a problem with refresh rate that can't handle by monitor? video card? or ubuntu?

anyway i will try it on other PC and make an update later.

thanks

---

### Post by samantha on 2006-07-12
just try in other PC:

specs:
P IV 1.6GHz
ASusTek P4VP-MX
512MB DDR266
40GB Hardrive
17" Compaq S700 Monitor
Built-In S3 Display from VIA Chipset. 

& works fine. :mrgreen: 

now what could be the problem of my first rig?

---

### Post by AZzKikR on 2006-07-12
I see your first rig has an ATI card. I had somewhat the same problems like you did (bootup succeeds, until X was about to start). My screen just froze and I could not do anything else. 

The solution was to boot up in safe-graphics mode (it uses the VESA graphics driver instead of the ati driver), then install Ubuntu, and then download the fglrx driver for the ATI card. 

But it's strange that your rig won't boot up, even though you selected safe-graphics mode...

---


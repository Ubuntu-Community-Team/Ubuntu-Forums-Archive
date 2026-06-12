---
title: "Replacing motherboard"
date: 2006-02-27
forum: Desktop Environments
---

### Post by arden on 2006-02-27
My motherboard died yesterday. Powers up and I get a good beep code, but have no signal to the monitor. Tried 3 different vidio cards and no go. My question is can I replace my motherboard without reinstalling Breezy? I have done this before with windows as long as the chipsets were the same and had no problems. Is this the same in Linux or would it matter if it is a different chipset?   Thanks in advance.

---

### Post by xmastree on 2006-02-27
It should work, but I can't help thinking that if theres' a beep code, it's not dead... :-k

Have you tried resetting ther cmos? Usually a jumper near the battery.

Also, are you sure it's not the monitor.

---

### Post by taurus on 2006-02-27
Was that a short one beep or three beeps?  Try removing your RAMs and put them back in again...  I would check everything to make sure it's really the mobo before I replace it.

---

### Post by wylfing on 2006-02-28
I would really have to agree that this sounds like your monitor is dead, not the motherboard. You should be getting a "problem" beeping (often 3 beeps) if the motherboard is aggravated about the video output.

But, if you are sure the answer is replacing the motherboard, yes, you can swap motheboards even with different chipsets -- sometimes wildly different chipsets -- and Ubuntu will take it like a champ. It's a **lot** more resilient than Windows in this regard, in my experience. (Hint: Never, ever swap a non-RAID board with a RAID board under Windows. Under Linux this is typically OK.)

---

### Post by bigken on 2006-02-28
go to bios makers web site to what find out what the beep code error means or google it and it will tell what the problem is 9 time out of ten its ram ;)

---

### Post by ngms27 on 2006-02-28
I disagree, XP is easy to fix. It only fails because XP supports 4 different IDE controllers and installs only one on Setup. You can actually install the others.

Failing that put in the CD and do a repair if it bluescreens. Takes time but I have a 100% sucess record doing this to create images on different hardware in the Education sector.

I've never tried it on Ubuntu!!!

JonnyT

---

### Post by bigken on 2006-02-28
how can he do a repair insatall if the thing wont post ?

---

### Post by xmastree on 2006-02-28
[QUOTE=bigken]how can he do a repair insatall if the thing wont post ?[/QUOTE]
I think ngms27 was referring to wylfing's comment that XP is easy to break by installing a new motherboard.

However, the OP does mention a '**good** beep code', which is why I think the motherboard may not be the problem.

---

### Post by bigken on 2006-02-28
if hes running bent software it will if its genuine he should be ok ;)

---

### Post by bigken on 2006-02-28
[quote=bigken]if hes running bent software it will if its genuine he should be ok ;)[/quote]it will ask to be recativated

---

### Post by thespazzz on 2006-02-28
This dosen't sound like a MB issue to me.  If its having an issue initializing the Video Card or the Ram or if its broke it should give you an error beep code or nothing at all.  Is the Video onboard?  If so you may need to reset the CMOS to allow it to initialize another card rather than the onboard video.

---

### Post by arden on 2006-02-28
OK a little more info. I get a short single beep code just like everything is ok. I know the monitor is good, I tried it with a different computer. I tried resetting the cmos and nothing. The vidio cards work in a different computer. Only thing I havent tried yet is the ram, but thought I would get a bad beep code if the ram was bad. I will try the ram tonight after work. The monitor just has a no signal message when I turn the computer on. You can tell the computer is booting, the CD rom lights normally, and you can hear the harddrive spin up. Almost forgot to mention I even tried a different monitor and the same message no signal.

---

### Post by taurus on 2006-02-28
Is that an onboard video card or a PCI one?  See if you can find a PCI video card and connect your monitor to that!  It doesn't sound like your mobo is going south at all...

---

### Post by arden on 2006-02-28
The motherboard is a IWILL KK266 and does not have onboard vidio. The vidio cards I have been trying are AGP. I will have to look around and see if I have a PCI card and give it a try.

---

### Post by az on 2006-02-28
You can disconnect the power to the computer and remove the battery on the MB for about 30 seconds and see if wiping the memory fixes the problem - it could be that the CMOS is corrupt.

If you have to change your MB, the ide, sound and most other drivers are loaded on boot,  so that won't be a problem.  The video will be screwed up and you will have to reconfigure it manually.

Boot into recovery mode and run


dpkg-reconfigure -phigh xserver-xorg

and then run
init 2

---

### Post by arden on 2006-03-01
I have tried all suggestions still no go. I tried a different motherboard and processor, problem is it's a slot A processor and motherboard instead of a socket A and it boots but does not run long enough for me to reconfigure xorg before it reboots. I think I will have to reinstall from scratch or find a motherboard with a VIA 133A chip.

---

### Post by xmastree on 2006-03-01
It reboots? So presumably before it does that, all seems well?

Fire it up and run memtest (should be an option in the boot menu). What's the memory config?

---

### Post by coolclassic on 2006-03-01
My motherboard seems to be failing too, it gives 8 beeps (repeating) whilst trying to boot. I switch computer on 2 -5 times and it boots. According to MB websights the error code sudjests failing video card agp. I have replaced with spare cards but have same error. Is the error codes correct or is there other areas I should explore before purchasing new board.

---

### Post by thespazzz on 2006-03-01
[QUOTE=coolclassic]My motherboard seems to be failing too, it gives 8 beeps (repeating) whilst trying to boot. I switch computer on 2 -5 times and it boots. According to MB websights the error code sudjests failing video card agp. I have replaced with spare cards but have same error. Is the error codes correct or is there other areas I should explore before purchasing new board.[/QUOTE]

It could be that the AGP slot has become damage on the board.  Try using a PCI video card or the onboard video card if availiable and boot the machine.

---

### Post by arden on 2006-03-02
I tried running the mem test, can make it sometimes through test5 with no problems before a reboot. Was able to boot Breezy and even ru the update before a reboot. Thought it could be overheating so I cleaned and reapplied heatsink compound, still same problem. I gues it's time to find another motherboard. I really didn't want to run the slot A board anyway, just thought I could get bye till I found another socket A board with a VIA 133 chip.

---

### Post by akiro.yamamoto on 2006-03-02
[QUOTE=arden]I tried running the mem test, can make it sometimes through test5 with no problems before a reboot. Was able to boot Breezy and even ru the update before a reboot. Thought it could be overheating so I cleaned and reapplied heatsink compound, still same problem. I gues it's time to find another motherboard. I really didn't want to run the slot A board anyway, just thought I could get bye till I found another socket A board with a VIA 133 chip.[/QUOTE]

Why get another Socket A MB?
I would get a Socket 754 MB and CPU. Check pricewatch, a good combo only costs
around USD $100. That is with a AMD Sempron 64 2500+ CPU and a
ECS 755-A2 Socket 754 MB with SATA support. 
That is a combo that is a much better value that a Socket A set-up.

---

### Post by bigken on 2006-03-02
I totally agree with akiro.yamamoto go for a 64 bit mobo cheep as chips and very fast also very upgradable spend a few pounds more on sempron 3000
and a board with pci E

---

### Post by arden on 2006-03-02
Thing is this is not my main computer and I have several socket A processors and a lot of sdram. Not really ready to go linux solo, but I think i' close except for my games. I have an  MAME machine for arcade games, but still have alot of racing games I play on my main computer. I do not run XP, I took XP off and only run W2K for me I have had much less problems.

---


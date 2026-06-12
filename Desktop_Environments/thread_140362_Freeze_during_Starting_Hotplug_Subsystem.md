---
title: "Freeze during Starting Hotplug Subsystem"
date: 2006-03-06
forum: Desktop Environments
---

### Post by r3bol on 2006-03-06
Just installed Ubuntu &#8211; had some problems reading off the CD when installing (first install part). The first error was a read error (couldn&#8217;t read from the CD) when installing the base stuff and required me to repartition again. Second and third errors where general reading fails from the CD that just required me to repeat that install step. I did manage to get through it though.

Second part (without CD) went smoothly. Went through installation and started Ubuntu. 

My first and continuing attempts to boot, freeze whilst &#8216;Loading Modules&#8217;.
The exact point is &#8216;Starting Hotplug Subsystem&#8217;.

I have nothing other than Ubuntu on my system.

My PC: 
Dell Latitude (Laptop)
PII 400MHz
128MB

Ubuntu:
Version 5.10 for PC

---

### Post by WretchedSpawn on 2006-03-06
all those read errors sound a little fishy... did you try running an integrity test on the cd? (it's one of the options on the installation menu)

---

### Post by r3bol on 2006-03-06
Yes, the integrity test failed. What's an integrity test? Is it testing the CD or CD drive? Sorry i'm a Linux Noob.

If it's the CD should I try burn it again at a lower speed?

---

### Post by r3bol on 2006-03-07
I burned the CD at 8x and had no problems with the first part of the install this time. But the second part (without CD) froze at the same point whilst Loading Modules. 

I got real brave and had a look at **Expert Mode**. I did the Integrity Check again, which had more to it than the other one. It was interesting to see this…

> Some PCMCIA hardware needs special resource configuration options in order to work, and can cause the computer to freeze otherwise. For example, some Dell Laptops need “exclude port 0x800-0x8ff” to be specified here. These options will be added to /etc/pcmcia/config.opts. See the instruction manual or the PCMCIA HOWTO for more information.

So I specified “exclude port 0x800-0x8ff” in the space it gave me and it detected the CD-ROM drive and its contents (Breezy Badger). It then performed the Integrity Check and **passed**\\:D/ . 

Finally it took me back to the menu screen, which was kind of confusing because I didn’t know if I should continue with the “exclude port 0x800-0x8ff” parameters or go back to none expert mode and whether or not I could include it as a boot parameter. So I restarted and typed 
linux exclude port 0x800-0x8ff
at the boot prompt. This seemed to take ok (no errors at least).

So did it work???

Err, No:-k .
Same problem.

---

### Post by 1002285 on 2006-04-24
Interesting, I have the same computer and the same problem. So has anyone found out anything useful about it?

---


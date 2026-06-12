---
title: "Dell Latitude D620 random shut offs ubuntu 10.10"
date: 2010-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by proyectomx on 2010-10-21
Hi.

I have a dell latidude d620 with nvidia graphic card:
VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

I am using ubuntu 10.04 since it came out, but when trying to boot livecd, liveusb or try to install ubuntu 10.10 (when I can), the computer randomly shuts off. no shutdown, no nothing, just turns off by itself.

Sometimes it makes it after a few minutes, it doesn't give me enough time to install... sometimes it takes a little while, letting me install.

When I finally could install, I thought this could be an issue that might have been solved with some updates, but no.... all updates installed. I tried graphic drivers from repositories and graphic drivers from nvidia website... no luck.

I had to go back to ubuntu 10.04, where I can finally have stability.

I don't have the logs in hand right now, but I remember I saw some kernel errors in one ocassion before shutting off. 

In some ocassions it starts getting slow until it shuts off, in other occassions it just shuts off with no aparent reason.

Does anyone have any idea of what might be happening?

---

### Post by ThaKidChillz on 2010-10-21
well idk how different the d620 is from the d610 which im using but im not having that problem with my setup since i installed 10.10. i am having usb and wifi issues though.

---

### Post by martin42 on 2010-10-21
Hi,

I have two Dell Latitude D620's with NVidia cards.  10.10 just works for me!  Both D620's installed 10.10 perfectly from CDROM (except that the Netbook edition starts the Desktop GUI, but that's another forum thread).

Have you taken the latest BIOS from [www.dell.com/support?](www.dell.com/support?)  It is from 2009 I think.  Maybe it fixes something.

Is the battery charged when you start?  Is the mains power on?  Is the BIOS reset to defaults, with no crazy BIOS power management setting?

Perhaps the Wireless card might be a problem.  I never like Dell's wireless cards, so I always throw them away and install Atheros card instead.  I like cards that aren't too new, otherwise it's difficult to find drivers.  But I left those D620's at work today, so I can't tell you which wireless cards I used.  You could try disabling the wireless cards, or perhaps removing them: it's easy to remove the keyboard if you're careful, following the Dell service instructions on their website.   (I am not known for my hardware skills, so with a bit of care, it's easy to change WiFi cards or RAM sticks under the keyboard on the D620.)

Good luck!

- Martin

---

### Post by martin42 on 2010-10-21
PS, the Dell D620 is not a 64-bit machine (my laptops are Core Duo, not Core 2 Duo), so the standard 32-bit x86 ISO CDROM must be used.

---

### Post by proyectomx on 2010-10-22
Hi.

I have the latest bios, which for my laptop is A10, dated 5/19/2008.
I haven't changed power management settings in bios, should I?
I am using a 32 bit iso to boot ubuntu. Attached is my hardware specs.

and the wireless card is intel, but it doesn't matter if I turn it off, it still does the same.

PD. the computer starts doing it sooner if I start using several applications at the same time... it starts getting slow, until it just shuts off, I think the fan starts blowing at full speed.

Once I opened a terminal from ubuntu to see if something appear in the logs before shutting off, and I only remembered seeing Kernel errors.


any other ideas of what might be causing the problem?

---

### Post by mörgæs on 2010-10-22
This sounds like the CPU overheating. As a safety measure, the BIOS (not Ubuntu) shuts down the machine. 

Have you tried to vacuum clean the air channels, plain and simple? If that does not help, I would stick to 10.04.

---

### Post by TBABill on 2010-10-22
I keep seeing more and more heat related posts for 10.10 lately. I'll wait a while longer or just stick to 10.04.

---


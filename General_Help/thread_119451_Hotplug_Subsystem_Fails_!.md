---
title: "Hotplug Subsystem Fails !"
date: 2006-01-19
forum: General Help
---

### Post by chicken-man on 2006-01-19
Hi, I've used ubuntu Linux before, but today I've installed it on my new PC, I am dual booting with Windows XP Professional.

After I done the first part I had to reboot, when I started booting ubuntu from the hard disk it got stuck on Hotplug Subsystem and would go no more, I have managed to bypass this by pressing CTRL+C a lot but then other things such as X don't work, I cannot set the root password as well.

Can some one please tell me what the problem is and how I can fix it, as I would like to use Linux very much.

System Information:

Intel Pentium 4 - 519 - 3.06ghz
Chipset: Intel 915P
MotherBoard: Sunshine DDR2 (GA-8I915PMD) Ver 0.1
DVD: HLDS GWA-4164B
Video: nVidia GeForce 6200SE/TC 256MB
RAM: DDR2-533 1024MB
HDD: Seagate Alpine Puma S-ATA 160GB
Audio:RealTek ALC880

---

### Post by chicken-man on 2006-01-19
Come on I'm in need of help :(

---

### Post by simon_is_learning on 2006-01-19
Do you have any USB-devices plugged in?

If thats the case, take em' away...

I had the same problem with an USB-Ethernet device

---

### Post by chicken-man on 2006-01-19
All are unplugged I have also tryed disableing the USB controller, but still no luck

---

### Post by Chade on 2006-01-19
I encountered this problem today as well!
It is on my grand fathers computer and I guided him throught the update applet to get the lates updates.
After the update he couldn't get on the net, and after some time on the phone I realized it was the hotplug sub system that failed.

He has a USB printer connected, and when he disconnected the printer the hotplug sub system loaded without problems...

Which of the latest updates packages could have caused this?

---

### Post by chicken-man on 2006-01-19
None it's just been installed

---

### Post by allegedly on 2006-01-19
Have the same problem as original post, only on a old intel PII box. Cntl-C gets me working fine - but is an irritation.

From what I have read on wiki and other post I understand that this kind of thing may be got around with either Kernel arguments in grub, or by editing the blacklist file associated with hotplug - but being a novice to Linux I'm a bit out of my depth, and need someone to explain to me how I work out what arguments/edits to make.

Am fairly certain that it's my ethernet card that hotplug doesn't like.

Anyone like to help?

---

### Post by blaise69 on 2006-01-19
Hi guys,  try following the advice given in the wiki on [BootHotPlugErrors]("https://wiki.ubuntu.com/BootHotPlugErrors?highlight=%28hotplug%29"), see if this works, and post your findings here.

Cheers,

Blaise.

---

### Post by allegedly on 2006-01-19
Will try this if I can't find any more info, but I don't know what shpchp and pciehp modules are, and am fairly convinced that it is my network card that is fouling things up - this fix looks like a very general 'fix' rather than getting to the real problem.

---

### Post by chicken-man on 2006-01-20
Hmmm I reinstalled ubuntu (server) this time when I boot it I get a load of hex codes and other rubbish, at the end I get this message:
<3>hw_random: RNG Not Detected :???:

---

### Post by Chade on 2006-01-25
No solution yet?
It came to my mind a couple of days ago that I got this same problem when I first installed the printer (Brother HL2030 USB laser printer), and I'm pretty sure that the solution was to add some kernel parameter in grub's menu.lst.
BUT - then I upgraded to a newer kernel and the menu.lst file seems to have been overwritten and I can't remember what kernel parameter it was, and I can't seem to find it again!

As of now, I can boot the computer when the printer isn't connected, I can connect the printer when the computer is running and print one print job, but the the entire system hangs (or at least X) and I have to shut it down the hard way...
If I boot the computer with the printer connected, the hotplug subsystem doesn't load and thus none of the PCI cards (sound and network) works... 

Can someone please help me!?!

/soon desperate after N hours of fruitless googling...

---

### Post by AndyCooll on 2006-01-25
Before people jump in, just want to query whether it is truly the hotplug system or in actual fact Alsa?

I query this because I can't get my USB wireless to work and though it seems to hang on "Hotplug", I've read somewhere that the actual problem is related to Alsa, i.e the function that follows Hotplug on boot-up.

---

### Post by oopsz on 2006-01-25
Your problem is ALSA.  add snd_hda_intel to /etc/hotplug/blacklist.

I'm still not sure how to fix it until dapper is released.

---

### Post by oopsz on 2006-01-25
If blacklisting snd_hda_intel fixes your problem, you can get sound working by following the instructions here:
[http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html](http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html)
:D

---


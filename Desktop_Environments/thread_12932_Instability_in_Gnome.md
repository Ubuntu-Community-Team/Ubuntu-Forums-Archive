---
title: "Instability in Gnome"
date: 2005-01-27
forum: Desktop Environments
---

### Post by freshdaemon on 2005-01-27
Hello Ubuntu users,

I'm having some problems with seemingly random lockups. The symptoms are always the same: the keyboard and mouse suddenly stop responding, the sound (if there is any) starts stuttering and all graphics stop updating, no corruption, but any animation will be "frozen". Since I can't kill the X server all I can do is hit reset.

They don't seem to follow a particular app or apps. Firefox seemed to do this so I uninstalled it and used Epiphany instead, however, sometimes now it has locked up while viewing a movie in Xine, checking mail in Evolution, and quite a few times it has locked up at the logon screen before I've even had a chance to type my username in!

I have run a battery of hardware tests to eliminate a hardware fault. I have booted from a Knoppix LiveCD and run CPU Burn-in at the same time as streaming radio with XMMS, so as to work the CPU, network and sound. This ran fine for hours without a single hiccup. I also ran 7 passes of Memtest86, which found no errors either. Then I ran Hitachi's hard-drive health tests on all my drives, which also found no errors.

I have run Yoper on this system (built from Linux From Scratch and using KDE as the desktop) for some time without any problems, but I like Ubuntu better. I just wish it would stop crashing!

I'm quite new to Linux, but I know my way around a shell. What should I look for? The kernel messages don't contain anything useful. I have updated all packages including the kernel to the latest versions and disabled APIC (my system is quite old and it might have been causing problems, I thought). Beyond that I'm stumped.

Thanks in advance for your help.

---

### Post by jdodson on 2005-01-27
[QUOTE=freshdaemon]Hello Ubuntu users,

I'm having some problems with seemingly random lockups. The symptoms are always the same: the keyboard and mouse suddenly stop responding, the sound (if there is any) starts stuttering and all graphics stop updating, no corruption, but any animation will be "frozen". Since I can't kill the X server all I can do is hit reset.

They don't seem to follow a particular app or apps. Firefox seemed to do this so I uninstalled it and used Epiphany instead, however, sometimes now it has locked up while viewing a movie in Xine, checking mail in Evolution, and quite a few times it has locked up at the logon screen before I've even had a chance to type my username in!

I have run a battery of hardware tests to eliminate a hardware fault. I have booted from a Knoppix LiveCD and run CPU Burn-in at the same time as streaming radio with XMMS, so as to work the CPU, network and sound. This ran fine for hours without a single hiccup. I also ran 7 passes of Memtest86, which found no errors either. Then I ran Hitachi's hard-drive health tests on all my drives, which also found no errors.

I have run Yoper on this system (built from Linux From Scratch and using KDE as the desktop) for some time without any problems, but I like Ubuntu better. I just wish it would stop crashing!

I'm quite new to Linux, but I know my way around a shell. What should I look for? The kernel messages don't contain anything useful. I have updated all packages including the kernel to the latest versions and disabled APIC (my system is quite old and it might have been causing problems, I thought). Beyond that I'm stumped.

Thanks in advance for your help.[/QUOTE]


hrmmm, what kind of video card do you have?  what kind of motherboard?  do you have a acpi bios?

---

### Post by CowPie on 2005-01-27
[QUOTE=freshdaemon]Hello Ubuntu users,

I'm having some problems with seemingly random lockups. The symptoms are always the same: the keyboard and mouse suddenly stop responding, the sound (if there is any) starts stuttering and all graphics stop updating, no corruption, but any animation will be "frozen". Since I can't kill the X server all I can do is hit reset.

They don't seem to follow a particular app or apps. Firefox seemed to do this so I uninstalled it and used Epiphany instead, however, sometimes now it has locked up while viewing a movie in Xine, checking mail in Evolution, and quite a few times it has locked up at the logon screen before I've even had a chance to type my username in!

I have run a battery of hardware tests to eliminate a hardware fault. I have booted from a Knoppix LiveCD and run CPU Burn-in at the same time as streaming radio with XMMS, so as to work the CPU, network and sound. This ran fine for hours without a single hiccup. I also ran 7 passes of Memtest86, which found no errors either. Then I ran Hitachi's hard-drive health tests on all my drives, which also found no errors.

I have run Yoper on this system (built from Linux From Scratch and using KDE as the desktop) for some time without any problems, but I like Ubuntu better. I just wish it would stop crashing!

I'm quite new to Linux, but I know my way around a shell. What should I look for? The kernel messages don't contain anything useful. I have updated all packages including the kernel to the latest versions and disabled APIC (my system is quite old and it might have been causing problems, I thought). Beyond that I'm stumped.

Thanks in advance for your help.[/QUOTE]
 Oh i think I saw this on the rage3d.com ATI message boards?  Do you have an ATI card?

---

### Post by freshdaemon on 2005-01-27
The graphics card is an NVidia GeForce DDR. I'm running the 1.0-6111 NVidia propietary drivers. 

The motherboard is an ABit BP6 with an RU BIOS. It does support ACPI (at least, under Windows 2K/XP it will sleep, suspend and soft power-off) but I have read that Linux kernels regard ACPI as unstable on an SMP box, so I have disabled ACPI in Lilo.

---

### Post by dare2dreamer on 2005-01-27
I had no end of problems with memory running out of control, systems lockups and the like on an ASUS motherboard until I added the following kernel options to my grub config:

```
pci=biosirq mem=nopentium noapic nolapic acpi=off noacpi=off apm=off
```

Since then, I've had no issues whatsoever.

Ya might give it a shot. If it works, add apm to /atc/modules so your machine still powers off on shutdown.

---

### Post by freshdaemon on 2005-01-28
OK, I purged lilo, installed grub and added your suggested kernel options to mine. So far so good, at least, the system boots! I suppose the only thing to do is to test for a while and see if the instability has gone. I'll post back with my results. Thanks again!

---

### Post by freshdaemon on 2005-01-28
It doesn't look like that worked - it just locked up again, exactly as before. I was browsing in Epiphany and listening to XMMS. What else can I try?

---

### Post by freshdaemon on 2005-01-28
Something else springs to mind. It seems that the system will only crash when I'm actively using it. If I leave it alone for hours, even if it's downloading, playing music and running CPU Burn-in to 100% CPU useage, it won't crash. Is it possible that there's something wrong with the input component of the X server and this is causing instability? How would I check that?

---

### Post by freshdaemon on 2005-01-29
Another update. This time I have something verbose to report. I tried running without X started. I wanted to make sure the system was being worked, so I started cpuburn-in and hit Ctrl-Z to shift it to the background, and I was greeted with:

> unable to handle kernel NULL pointer dereference 

and that was it - no further information. The cursor continued to blink, but the system had hard-locked and I had to hit the reset switch. Searching Google seems to indicate that this may be a problem with the way the kernel has been compiled, but it also seems that there should be more information listed along with this error.

What to do now? I'm trying to duplicate the fault, hoping that it might give more information next time, but so far all is well (naturally!).

---


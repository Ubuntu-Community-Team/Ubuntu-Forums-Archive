---
title: "PCI: Cannot allocate resource region 1 of device 0000:00:14.0"
date: 2007-10-30
forum: Dell  Ubuntu Support
---

### Post by Ismail on 2007-10-30
[SIZE="3"][B]Hi,
I am Using Ubuntu 7.10 on Dell Optiplex 320, i have problem in booting when i boot from UBuntu CD it givesme  Error PCI: Cannot allocate resource region 1 of device 0000:00:14.0
aftre that it will stuck the system i cannot do any thing, if some one knows abut that error pleaeas tell me on my personal Mail address.:KS

[email]ismail@megaplus.com.af[/email]

thanks and Regards[/COLOR]
Muhammad Ismail[/B][/SIZE]

---

### Post by clarkni5 on 2007-11-01
I ran into the same problem last night on my brand new Dell Optiplex 320. Have you found a solution?

I was using the standard x86, 32-bit, installation CD. Tonight I am going to try the 64-bit installation CD. My machine has a Core 2 Duo processor and some of the other forum posts that I have seen suggest that people are using the 64-bit installation CD.

It looks like other people have successfully installed Ubuntu on their Dell Optiplex 320 but still had to change their boot loader to LILO, per this thread:
[http://ubuntuforums.org/showthread.php?t=409345]("http://ubuntuforums.org/showthread.php?t=409345")

If anyone has any more insight, I would greatly appreciate your input. I would really like to get Ubuntu running on my new computer.

To summarize the problem, the installation CD will bring up the boot menu but will not boot the live CD, throwing this error while loading the kernel:
PCI: Cannot allocate resource region 1 of device 0000:00:14.0

I have tried using several boot parameters, including pci=nomsi, noapic, and nolapic, but they have not resolved the problem.

---

### Post by clarkni5 on 2007-11-01
I also found this posting, suggesting that adding hpet=disable to the boot options will resolve the problem:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138305]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/138305")

I will try this tonight, as well.

The problems appears to be related to the SB600 chipset and is probably a kernel issue and not a problem with Ubuntu.

---

### Post by clarkni5 on 2007-11-01
Using the hpet=disable boot parameter did allow me to boot the live CD.

---

### Post by sonam on 2008-04-01
Hi,
I am also using Dell Optiplex 320, trying to install Ubuntu 7.10  and facing same problem as u guys.... "the soft lock up" 
It is my 100th time installing and removing.. 


Interesting enough the same problem occurs for Fedora core 7.
Following messages are displayed: 

PCI: MSI quirk detected. MSI deactivated.
ClockSource tsc unstable (delta = -297336209339 ns)
Time: hpet clocksource has been installed. 


After that nothingness :)


what does it mean? Anyone able to solve it?


Windows 2000 and windows XP are installed with no problem.... this is NOT good.  ;)

---


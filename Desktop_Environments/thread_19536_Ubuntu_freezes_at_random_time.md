---
title: "Ubuntu freezes at random time"
date: 2005-03-12
forum: Desktop Environments
---

### Post by Roman2K on 2005-03-12
Hi all,

I just installed Ubuntu warty, all my hardware look to have been recognized and to work well, this is incredible 8). The desktop is impressively clean, I love that.

The PC is a laptop Sony VAIO PCG-K295HP, and the problem is that it completely freezes at a random time : I mean the keyboard and the mouse don't respond, nothing moves on the screen, and if the freeze happens when the HDD led is lit, it stays lit.

I didn't notice anything strange in the /var/log/syslog except something like "ACPI-1133: *** Error: Method execution failed \_SB_.PCI0.LPCB.LNKU._CRS..." (this is maybe not the exact string but it looks like that, I took it from another webste) but maybe I'm wrong because I'm a newbie.

This is really annoying, impossible to use the PC properly :(, I really don't know what to do and I hope you will help me.

EDIT: I also tried made an apt-get update and apt-get upgrade with only the 2 lines concerting Ubuntu security in /etc/apt/sources.list but it didn't change anything.

Thanks a lot in advance.

---

### Post by GrapeApe on 2005-03-12
The easiest thing to try is to add acpi=off to your boot command line (if acpi is causing the problems, which at first glance it appears to be).

I would just bring up the command line when grub loads and add acpi=off to the end of the command.

PS: When you bring up the grub menu (hitting ESC), you can edit the entry by hitting the "e" key.

---

### Post by Roman2K on 2005-03-12
[QUOTE=GrapeApe]The easiest thing to try is to add acpi=off to your boot command line (if acpi is causing the problems, which at first glance it appears to be).

I would just bring up the command line when grub loads and add acpi=off to the end of the command.

PS: When you bring up the grub menu (hitting ESC), you can edit the entry by hitting the "e" key.[/QUOTE]
Thank you for your fast answer. I'm going to try it and report the result, thank you.

---

### Post by Roman2K on 2005-03-12
I don't know what you meant with "bring up the commandline when grub loads" but I managed to add acpi=off to the line "kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash" in the file /boot/grub/menu.lst

Then I restarted the PC and ACPI looks to be disabled because the battery icon in the tray is grayed, as same as the Wireless state.

It has not frozen yet but I need the wireless connection and disabling acpi also disable my wireless interface : ath0.

What can I do to have my ath0 back while having acpi=off (if it doesn't crash with this parameter) please ?

**EDIT:** if the problem was still here, it would have been crashed now, so I think it doesn't crash anymore. Now the problem is to get the ath0 and the power management back, can you help me ?

Thanks

---

### Post by Roman2K on 2005-03-12
Please...

Can you help me ?

I really need your help to make my wifi card work while I have ACPI=off (if it is not off, the PC freezes after a random time after it has started).

Thank you in advance.

---

### Post by Roman2K on 2005-03-13
Please ? 8-[
And would the patches on [http://acpi.sourceforge.net](http://acpi.sourceforge.net) avoid the freezes when acpi is not disabled ?

---

### Post by ManiacMac on 2005-03-16
This may help as well 

[http://ubuntuforums.org/showthread.php?t=20393](http://ubuntuforums.org/showthread.php?t=20393)

---

### Post by jamin_l on 2005-03-17
I'm also having random system freezes for apparently no reason. However I'm not running a laptop. Running Hoary here.

Attached a copy of /var/log/syslog as a text file.

If it doesn't post here, check this URL: [http://members.shaw.ca/c_nikkel/syslog.txt](http://members.shaw.ca/c_nikkel/syslog.txt)

---

### Post by ManiacMac on 2005-03-17
next time that happens, open a terminal and check top.  I know this may take up to 10-15 min to complete, but that would see what process is causing the problem.

---

### Post by jamin_l on 2005-03-17
I can't open a term while it's frozen. The mouse moves, but absolutely nothing is responsive. not even Alt-Shift-F2 (I think that's the combo) to go out of X-Win. That's why I've posted the syslog.

---


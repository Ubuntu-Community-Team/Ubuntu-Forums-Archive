---
title: "Repeated crashes - error log attached"
date: 2008-02-27
forum: Desktop Environments
---

### Post by skydiverQ on 2008-02-27
Hi all,

Relatively new installation of Xubuntu, 7.10.  I am getting random system crashes requiring me to power off the CPU and restart.  I learned in another topic how to print out the logs, and I noticed that I was getting the same series of entries every time immediately before a crash.  Here is a sample:

**************

Feb 27 03:27:04 desktop-old-dell kernel: [   22.260000] pnp: Device 00:08 activated.
Feb 27 03:27:04 desktop-old-dell kernel: [   22.260000] parport_pc 00:08: reported by Plug and Play ACPI
Feb 27 03:27:04 desktop-old-dell kernel: [   22.260000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
Feb 27 03:27:04 desktop-old-dell kernel: [   23.288000] PCI: Enabling device 0000:00:0d.0 (0104 -> 0105)
Feb 27 03:27:04 desktop-old-dell kernel: [   23.292000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Feb 27 03:27:04 desktop-old-dell kernel: [   23.292000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 27 03:27:04 desktop-old-dell kernel: [   24.352000] lp0: using parport0 (interrupt-driven).
Feb 27 03:27:04 desktop-old-dell kernel: [   24.464000] Adding 2265124k swap on /dev/sda5.  Priority:-1 extents:1 across:2265124k
Feb 27 03:27:04 desktop-old-dell kernel: [   25.068000] EXT3 FS on sda1, internal journal
Feb 27 03:27:04 desktop-old-dell kernel: [   27.020000] No dock devices found.
Feb 27 03:27:04 desktop-old-dell kernel: [   27.264000] input: Power Button (FF) as /class/input/input4
Feb 27 03:27:04 desktop-old-dell kernel: [   27.264000] ACPI: Power Button (FF) [PWRF]
Feb 27 03:27:05 desktop-old-dell kernel: [   29.864000] ppdev: user-space parallel port driver
Feb 27 03:27:06 desktop-old-dell kernel: [   30.272000] audit(1204100825.754:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4440 profile="/usr/sbin/cupsd"
Feb 27 03:27:06 desktop-old-dell kernel: [   30.372000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Feb 27 03:27:06 desktop-old-dell kernel: [   30.372000] apm: overridden by ACPI.
Feb 27 03:27:06 desktop-old-dell kernel: [   30.756000] Failure registering capabilities with primary security module.
Feb 27 03:27:06 desktop-old-dell dhcdbd: Started up.
Feb 27 03:32:48 desktop-old-dell syslogd 1.4.1#21ubuntu3: restart.
Feb 27 03:32:48 desktop-old-dell kernel: Inspecting /boot/System.map-2.6.22-14-generic
Feb 27 03:32:48 desktop-old-dell kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Feb 27 03:32:48 desktop-old-dell kernel: Symbols match kernel version 2.6.22.

************

new info:  It appears as though starting up gtk-gnutella will pretty much regularly invoke one of these crashes.  Not immediately, but 20 or so seconds after starting it....

also, fsck did report some errors, but they were fixed manually.  I also tried removing dhcdbd, and tried the restricted drives for my nvidia.  None of these seemed to have any impact.  The crash sometimes happens during bootup, when the bar is mabye 1/8 of the way complete.

If additional entries are necessary, I have attached a larger log to this post.  I ayone needs the full log (~600k worth), I will be happy to email it.

I have no clue what is causing this, I'm a noob.  Thanks in advance!

-Q

---

### Post by cbiere on 2008-02-27
It could be a thermal problem or bad RAM. You should have an eye on the system and CPU temperature. Check your RAM with memtest.

---

### Post by skydiverQ on 2008-02-27
Thanks for the response Cbiere...

I have checked the memory, ran memtest through two full passes, and it was one hundred perecnt clear.  Also, I don't think it was thermal, I got so frustrated last night (that combined with the ease of installation) that I reinstalled the entire OS again, fully reformatting the (brand new) hard drive.  After doing this, I did the full updates, downloaded Epiphany again, and installed Limewire.  It ran all night just wonderfully, downloaded two full seasons of Entourage while I slept.  With zero issues.

These problems initially started to manifest themselves when I was trying to connect this machine to my MS Win network.  I remember installing pyneighborhood, samba, and gnome commander.  All three of these were eventually removed in an attmept to fix the crashes, however the programs left but the problem did not.

I am going to keep running my fresh install while installing nothing new, just to see what happens.  During that time, I'll have to figure out how to back up my config (kernal, whatever I call it now!) and at some point down the road, I'll try the network connection again.

I seem to be running into the same sort of problems that I was hoping Linux would have allowed me outgrow  :/

-Q

---

### Post by skydiverQ on 2008-02-29
UPDATE

The crashes returned, so I started playing with hardware.  Turns out my Dell Dimension XPS T700R did not like the combination of a Maxtor Ultra 133 controller and my AOpen Cobra AW850 sound card.  When I pulled the sound card, the random crashes disappeared.  If I reinsert it, they reappear.

This sound card is supposedly supported by Linux, is there anything I can potentially change (bios, etc.) in order to get it to work...?  Or am I buying a new sound card?

-Q

---

### Post by cbiere on 2008-02-29
You could try putting the cards into different slots. The IDE controller should be in a busmaster-capable slot, usually the first one. Make sure that no IRQs are shared. You could also try to reduce or increase the PCI latency timer in the BIOS.

---


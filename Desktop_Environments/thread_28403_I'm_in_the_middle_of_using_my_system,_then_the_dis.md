---
title: "I'm in the middle of using my system, then the display goes black??"
date: 2005-04-20
forum: Desktop Environments
---

### Post by dolson on 2005-04-20
This has happened many times, and I'm getting very sick of it.

My computer could just sit there, and it'll go black. I could be typing an email, and it'll go black. I could be trying to play a game, and it'll go black. I could be in bed sleeping, and it'll go black... And when I see it happen, I can't fix it - can't kill X, can't switch to another console, can't anything. Not even the magic SysRq combo works (I assume it's not disabled in Ubuntu kernels, but maybe I am wrong about that).

Anyhow, this is not an issue I ever had with Debian Sid, and at first I thought it was X.org, but then I remembered that it was happening with Warty as well. So that's not the issue.

I used Debian for a few years with no issues. I don't think my video card is dying on me (it's an NVIDIA GF4Ti4200 128MB and it's set up with dual monitors - both go black) because it only started happening very early on in my switch to Ubuntu.

Now, it doesn't happen daily, but maybe a few times a week. Or my system might go fine for a week or two. All I know is that with Sid, my uptimes on this system were almost always hovering around a month, with voluntary rebooting. Now that I've switched to Ubuntu, my best uptime is two weeks, and second best is only a week. Even my Windows system at work can pull of 20+ days at a time, surprisingly.

Simple solution would be to go back to Debian, but I'd rather not. I like Ubuntu, I want to see it succeed as THE desktop Linux, and I recommend it to all my friends. If I could just get this issue nailed down, I'd have no complains. Oh, and maybe toss in FreeCiv 2.0 to boot. ;)

---

### Post by heimo on 2005-04-20
Sorry to hear about the problems. I know how annoying that can get.
 
Anything in logs? Power management enabled? Could you try disabling power management (if it's enabled). Also you could run programs that test hardware malfunctions and stability (I think memtest86 or whats-it-called can be run from dos boot disk) could give some information or at least rule out issues.
 
Many hardware related problems can cause similar problems and can be very hard to track. If it's possible for you to swap some hardware (PSU* / memory), I'd try that.
 
:|
 
 
EDIT: *) for pc hardware newbies, PSU = power supply unit

---

### Post by dolson on 2005-04-20
My PC has been running reliably for a long time... On Debian.

Anyhow, I was going through the logs, as it just happened to me after burning a CD and then reinserting the disc... And then after a fresh boot, I inserted the disc, and it did it again. Earlier, when I posted this thread, it just happened out of nowhere when I was trying a demo of Darwinia. The last time it happened, the SysRq combos worked...

Anyhow, here is the section of the logs:

Apr 20 04:10:55 localhost gconfd (dana-8132): Resolved address "xml:readwrite:/home/dana/.gconf" to a writable configuration source at posit$Apr 20 04:11:17 localhost kernel:  [__report_bad_irq+42/143] __report_bad_irq+0x2a/0x8f
Apr 20 04:11:17 localhost kernel:  [handle_IRQ_event+46/100] handle_IRQ_event+0x2e/0x64
Apr 20 04:11:17 localhost kernel:  [note_interrupt+124/223] note_interrupt+0x7c/0xdf
Apr 20 04:11:17 localhost kernel:  [__do_IRQ+318/330] __do_IRQ+0x13e/0x14a
Apr 20 04:11:17 localhost kernel:  [do_IRQ+25/36] do_IRQ+0x19/0x24
Apr 20 04:11:17 localhost kernel:  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Apr 20 04:11:17 localhost kernel:  [__do_softirq+47/135] __do_softirq+0x2f/0x87
Apr 20 04:11:17 localhost kernel:  [do_softirq+38/40] do_softirq+0x26/0x28
Apr 20 04:11:17 localhost kernel:  [irq_exit+53/55] irq_exit+0x35/0x37
Apr 20 04:11:17 localhost kernel:  [do_IRQ+30/36] do_IRQ+0x1e/0x24
Apr 20 04:11:17 localhost kernel:  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Apr 20 04:11:17 localhost kernel: UDF-fs: No VRS found
Apr 20 04:11:34 localhost shutdown[8416]: shutting down for system halt
Apr 20 04:11:34 localhost uptimed: moving up to position 36: 0 days, 00:02:18
Apr 20 04:11:35 localhost gconfd (dana-8132): Received signal 15, shutting down cleanly
Apr 20 04:11:35 localhost gconfd (dana-8132): Exiting
Apr 20 04:11:37 localhost shutdown[8527]: shutting down for system halt
Apr 20 04:11:52 localhost kernel: SysRq : SAK
Apr 20 04:11:53 localhost kernel: SysRq : Emergency Sync
Apr 20 04:11:53 localhost kernel: Emergency Sync complete
Apr 20 04:11:53 localhost kernel: SysRq : Emergency Remount R/O
Apr 20 04:13:13 localhost syslogd 1.4.1#16ubuntu6: restart.

So, there it is... I don't know what else to try.

That only occurs once in the logs that I can see... But it locked 3 times in the last little while.

Checking earlier on in the logs, I see this:

Apr 20 02:31:40 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 20 02:31:40 localhost kernel: pnp: PnP ACPI init
Apr 20 02:31:40 localhost kernel: pnp: PnP ACPI: found 11 devices
Apr 20 02:31:40 localhost kernel: PnPBIOS: Disabled by ACPI PNP
Apr 20 02:31:40 localhost kernel: PCI: Using ACPI for IRQ routing
Apr 20 02:31:40 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
Apr 20 02:31:40 localhost kernel: ** causes a device to stop working, it is probably because the
Apr 20 02:31:40 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
Apr 20 02:31:40 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
Apr 20 02:31:40 localhost kernel: ** behavior.  If this argument makes the device work again,
Apr 20 02:31:40 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
Apr 20 02:31:40 localhost kernel: ** so I can fix the driver.
Apr 20 02:31:40 localhost kernel: pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
Apr 20 02:31:40 localhost kernel: pnp: 00:01: ioport range 0xe800-0xe81f has been reserved
Apr 20 02:31:40 localhost kernel: pnp: 00:0a: ioport range 0x290-0x297 has been reserved
Apr 20 02:31:40 localhost kernel: pnp: 00:0a: ioport range 0x370-0x375 has been reserved

lspci outputs this:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:00:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

cat /proc/interrupts shows this:

  0:     902715          XT-PIC  timer
  1:       4595          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  3:          0          XT-PIC  ehci_hcd
  4:          0          XT-PIC  libata, uhci_hcd, uhci_hcd
  8:          1          XT-PIC  rtc
  9:          1          XT-PIC  acpi
 10:      17767          XT-PIC  uhci_hcd, uhci_hcd, eth0
 11:      77521          XT-PIC  EMU10K1, nvidia
 12:      37628          XT-PIC  i8042
 14:      32677          XT-PIC  ide0
 15:        653          XT-PIC  ide1
NMI:          0
LOC:     902548
ERR:       1182
MIS:          0

Can anyone point me to the right direction? Is it the suggestion offered in the logs, to add pci=routeirq (I assume to the kernel config line)?

Thanks.

---

### Post by heimo on 2005-04-20
[QUOTE=dolson]Can anyone point me to the right direction? Is it the suggestion offered in the logs, to add pci=routeirq (I assume to the kernel config line)?
[/QUOTE]
 
That looks like good idea to try, and yes - it definitely looks like a kernel parameter. Those logs don't tell me much, maybe someone more familiar with subject can decrypt? :?

---

### Post by dolson on 2005-04-22
I guess no one knows?

---

### Post by dolson on 2005-05-05
Okay, so I rebooted again, and this time, it wouldn't even boot up anymore. It would start, but then the video would cut out... I tried it about 7 times. I tried booting the Warty live CD, but no go. I tried booting the install CD, but no go. I tried an old Gentoo 1.4rc CD that I had laying around, but the same thing - starts to boot, then goes to black. I tried a Windows XP CD (came with my laptop that I bought second hand, like I'd pay for that crap) and it booted up fine and started going through the process... I tried Ubuntu again a few times, still nothing. I tried pulling the video card, and replacing it with an older NVIDIA GF4MX and it booted on the first try... I still have more testing to do, but assuming that it's the fix:

This leads me to another question.

What is a decent dual-head video card that I should get, fairly cheap but new? I will be heading to this store, so if you can, suggest one from their list:

[www.canadacomputers.com](www.canadacomputers.com)

I hate ATI, but if they are highly recommended, then I'll go for it...

Thanks guys!

---


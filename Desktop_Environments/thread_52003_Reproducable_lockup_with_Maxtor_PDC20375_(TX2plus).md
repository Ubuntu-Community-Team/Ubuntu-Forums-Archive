---
title: "Reproducable lockup with Maxtor PDC20375 (TX2plus) and software raid"
date: 2005-07-26
forum: Desktop Environments
---

### Post by ioliver on 2005-07-26
I have 4x Maxtor PDC20375 SATA cards in PCI slots.
Each drive is cabled to 2 SATA HDs and these are used as two groups of four for software raid using mdadm.  I boot off a non-raid PATA drive.

It all works fine, but if I really stress the disk subsystem (a big copy and then a "du -sh" in a top level dir) I get
ata7: command timeout
and the system freezes solid.

This is a pretty vanilla Hoary install.

What information should I collect to help pin down this problem?
Where should I report it? (As a bug on the kernel? On libata?)
Any suggestions as to things to tweak to try and localise the issue?

hdparm is reporting -
/dev/sdd:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 250059350016, start = 0

Note that for some reason DMA isn't turned on. Should I force it to be on at boot?

Here is lspci
# lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
0000:00:0d.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
0000:00:0e.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:13.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)

Obvious things to try are -
1) Try and find an up to date bios for the mobo
2) Try acpi=off
3) Try and force dma on
4) ???

I'm open to suggestions for steps 4 to infinity!  

Regards

Ian

---

### Post by ioliver on 2005-07-26
Oh, and my log is stuffed with these -

Jul 25 17:33:42 localhost kernel: ata7: status=0x51 { DriveReady SeekComplete Error }
Jul 25 17:33:42 localhost kernel: ata7: error=0x0c { DriveStatusError }

Google offers up little regards error 0x0C

Regards

Ian

---

### Post by ioliver on 2005-07-26
It gets stranger. Below is the output of lspci -v for the four Promise cards. Notice that two have latency 96 and the last two (which I think are the two giving problems) have latency 32.

Perhaps it's also time to try and reflash the bios on the TX2plus cards. Another smoking gun is that the BIOS for the card(s) only spots four drives at boot time, so perhaps is only initialising two cards.

# lspci -v

0000:00:0c.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
        Subsystem: Promise Technology, Inc. PDC20375 (SATA150 TX2plus)
        Flags: bus master, 66MHz, medium devsel, latency 96, IRQ 19
        I/O ports at d800 [size=64]
        I/O ports at d400 [size=16]
        I/O ports at d000 [size=128]
        Memory at ed800000 (32-bit, non-prefetchable) [size=4K]
        Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [60] Power Management version 2

0000:00:0d.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
        Subsystem: Promise Technology, Inc. PDC20375 (SATA150 TX2plus)
        Flags: bus master, 66MHz, medium devsel, latency 96, IRQ 16
        I/O ports at b800 [size=64]
        I/O ports at b400 [size=16]
        I/O ports at b000 [size=128]
        Memory at ec800000 (32-bit, non-prefetchable) [size=4K]
        Memory at ec000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [60] Power Management version 2

0000:00:0e.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
        Subsystem: Promise Technology, Inc. PDC20375 (SATA150 TX2plus)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        I/O ports at a800 [size=64]
        I/O ports at a400 [size=16]
        I/O ports at a000 [size=128]
        Memory at eb800000 (32-bit, non-prefetchable) [size=4K]
        Memory at eb000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [60] Power Management version 2

0000:00:13.0 Unknown mass storage controller: Promise Technology, Inc. PDC20375 (SATA150 TX2plus) (rev 02)
        Subsystem: Promise Technology, Inc. PDC20375 (SATA150 TX2plus)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        I/O ports at 5800 [size=64]
        I/O ports at 5400 [size=16]
        I/O ports at 5000 [size=128]
        Memory at e9800000 (32-bit, non-prefetchable) [size=4K]
        Memory at e9000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [60] Power Management version 2

---

### Post by ioliver on 2005-07-27
Hmmm, I see someone else is having the same problem. In his case this is with an even never version of the kernel (but perhaps the libata backported to Hoary?)

[http://www.uwsg.iu.edu/hypermail/linux/kernel/0507.1/0651.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0507.1/0651.html)

The thought of having to join lkml to report this is rather scary!  
Should I put it in the ubuntu bugzilla?

Regards

Ian

---

### Post by ioliver on 2005-07-27
And to continue my monologue ...

I've tried acpi=off
I've tried turning on P&P OS in the BIOS.
I've tried the 2.6.12 kernel from Breezy.

All I need to do to trigger this is -
dd if=/dev/md1 of=/dev/null bs=1024
this starts filling /var/log/syslog with the 0x0c errors and if I leave it to run will lock the machine solid.

All suggestions welcome!

Ian

---

### Post by ioliver on 2005-07-28
Now on bugzilla

[http://bugzilla.ubuntu.com/show_bug.cgi?id=13046](http://bugzilla.ubuntu.com/show_bug.cgi?id=13046)

Ian

---


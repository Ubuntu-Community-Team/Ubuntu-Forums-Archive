---
title: "Monitor &quot;sleeps&quot; during reboot"
date: 2005-12-31
forum: General Help
---

### Post by Trizik on 2005-12-31
After installing Ubuntu, I am prompted to reboot. As soon as the reboot occurs, my monitor flicks off into "sleep" mode and never turns back on, so I am unable to see BIOS, GRUB, or anything else that appears during the first boot phase. I am forced to do a full hard boot in order to get a display on the monitor again. By full hard boot, I mean physically power down the computer, wait ~30 seconds, and power it back on. Instantly powering the computer off and on does not bring back the monitor's display.

The problem only occurs when I reboot after running the Ubuntu installer/booting into Ubuntu. It does not occur when I reboot after booting into Windows XP.

Specs:
AMD Athlon 64 3200+
ATI Radeon X800 XL
Ubuntu 5.10 (Breezy x86)

---

### Post by jdong on 2005-12-31
Does your BIOS have an option to re-post the video? If there are any options like that, activate them.

---

### Post by Trizik on 2005-12-31
No, it does not have a re-post video option.

---

### Post by jdong on 2005-12-31
from the bootparam manpage:
> 

`reboot=warm|cold,bios|hard'
(Only when CONFIG_BUGi386 is defined.) Since 2.0.22 a reboot is by default a cold reboot. One asks for the old default with `reboot=warm'. (A cold reboot may be required to reset certain hardware, but might destroy not yet written data in a disk cache. A warm reboot may be faster.) By default a reboot is hard, by asking the keyboard controller to pulse the reset line low, but there is at least one type of motherboard where that doesn't work. The option `reboot=bios' will instead jump through the BIOS. 




At the bootup menu, press ESC to get the full list, highlight your bootup choice, and hit "e" for edit. Find the line that starts with "kernel", press "e" again to edit it. At the end, add **reboot=cold,bios**. Press enter, and then "b" to boot the kernel. Try rebooting.

Repeat with different combinations of  {warm,cold} with {bios,hard} and see if any of those options will work better for you.

---

### Post by Trizik on 2005-12-31
[QUOTE=jdong]from the bootparam manpage:


At the bootup menu, press ESC to get the full list, highlight your bootup choice, and hit "e" for edit. Find the line that starts with "kernel", press "e" again to edit it. At the end, add **reboot=cold,bios**. Press enter, and then "b" to boot the kernel. Try rebooting.

Repeat with different combinations of  {warm,cold} with {bios,hard} and see if any of those options will work better for you.[/QUOTE]I tried all of the combinations. None of them work.

I noticed that whatever I add to the kernel line gets erased after reboot - is that supposed to happen?

---

### Post by jdong on 2006-01-02
[QUOTE=Trizik]I tried all of the combinations. None of them work.

I noticed that whatever I add to the kernel line gets erased after reboot - is that supposed to happen?[/QUOTE]

Yes, that is... Add it to /boot/grub/menu.lst and it'll stick.

---

### Post by Trizik on 2006-01-03
any other suggestions?

---

### Post by jdong on 2006-01-03
Please post more hardware info about your computer, and a **lspci -v** output. Try another Linux boot CD, too, like damnsmalllinux.org or Feather Linux or SLAX (all small ISO's), or even KNOPPIX. Does it happen with these?

---

### Post by Trizik on 2006-01-03
Hardware specs:> CPU: AMD Athlon 64 3200+ Venice 2000MHz
Motherboard: MSI RS480M2-IL
Memory: 2048 MB of mushkin PC 3200 DDR
Video Card: ATI X800XL 256MB 256-bit PCI-e Radeon
Hard Drive: Western Digital Raptor 74.0 GB @ 10000 RPMS
Monitor: Sylvania L17-BLK
CDR/CDRW Manufacturer & Model: Sony CRX320E
DVD R/W: NEC ND-3520Alspci -v output:> $ lspci -v
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 64
        I/O ports at 4100 [disabled] [size=32]
        Memory at <ignored> (64-bit, non-prefetchable)

0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: b0000000-cfffffff
        Capabilities: <available only to root>

0000:00:11.0 IDE interface: ATI Technologies Inc: Unknown device 437a (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
        I/O ports at fe00 [size=8]
        I/O ports at fd00 [size=4]
        I/O ports at fc00 [size=8]
        I/O ports at fb00 [size=4]
        I/O ports at fa00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <available only to root>

0000:00:12.0 IDE interface: ATI Technologies Inc: Unknown device 4379 (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        I/O ports at f900 [size=8]
        I/O ports at f800 [size=4]
        I/O ports at f700 [size=8]
        I/O ports at f600 [size=4]
        I/O ports at f500 [size=16]
        Memory at fe02e000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <available only to root>

0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374 (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375 (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373 (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 04)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: 66MHz, medium devsel
        I/O ports at 0400 [size=16]
        Memory at fe02a000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376 (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 64
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at f300 [size=16]
        Capabilities: <available only to root>

0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7141
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371 (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: fde00000-fdefffff

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 0080
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 11
        Memory at fe029000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 554d (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0302
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at fdd00000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at ef00 [size=256]
        Capabilities: <available only to root>

0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 556d
        Subsystem: ATI Technologies Inc: Unknown device 0303
        Flags: fast devsel
        Memory at fdd10000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at df00 [size=32]
        Capabilities: <available only to root>

0000:02:00.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 64
        I/O ports at de00 [size=8]
        Capabilities: <available only to root>

0000:02:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at fdcff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fdcf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 093c
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at dd00 [size=256]
        Memory at fdcfe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 093d
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at fdcfd000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at dc00 [size=128]
        Capabilities: <available only to root>I have not tried the other Linux boot CDs you mentioned, but I have tried: Linespire 5.0 boot CD, Ubuntu 5.10 (AMD64) boot CD, Ubuntu 5.10 (x86) boot CD, and Ubuntu 5.10 (x86) Breezy Badger, which is what I'm currently running. I will give the other boot CDs a try and report back.

---

### Post by Trizik on 2006-01-04
OK, I tried SLAX, Damn Small Linux, and Feather Linux and experienced the same problem.

Rebooting after booting into SLAX (nice distro btw!) resulted in a "sleeping" monitor.

I couldn't boot into DSL due to errors, but after rebooting, my monitor went into "sleep" mode again.

My computer froze while reading the Feather Linux CD and I was forced to reboot before reaching the boot screen. Sleeping monitor again...

I can get my monitor out of sleep mode by powering the PC off for 20-30 seconds and then powering it back on. Sometimes I even have to go as far as draining all power from the motherboard by removing the power supply's power cable from the wall socket and pressing the power button on the PC. Again, instantly powering the PC off and back on does not "awaken" the monitor.

I noticed that my keyboard also powers off when my monitor goes into "sleep" mode...

If you have any ideas at all, please share them. Thanks a lot.

---

### Post by jdong on 2006-01-04
Wait, so even if Linux doesn't load (i.e. Feather's situation) you still get a monitor blackout on reboot? This seems quite hardware related, the way it sounds.... hmm.... Windows might have some kind of workaround.

---

### Post by ysse on 2006-01-04
Could it be that you have a built-in video controller on the motherboard, which kicks in instead of your X800 when you reboot? If so, maybe there is a BIOS option to turn it off.

Or possibly, your X800 tries to use the DVI output instead of VGA or vice versa, don't know which one your monitor uses.

---

### Post by Trizik on 2006-01-04
[QUOTE=jdong]Wait, so even if Linux doesn't load (i.e. Feather's situation) you still get a monitor blackout on reboot?[/QUOTE]Right. With Feather, my computer seems to stall out when it's attempting to boot off the CD. My CDROM sounds and looks like it's reading the CD, but the rest of my computer seems unresponsive (it just sits at a BIOS-like screen without displaying any kind of activity). Rebooting/shutting down is the only way to get out of it, and that then results in a "sleeping" monitor.

[QUOTE=ysse]Could it be that you have a built-in video controller on the motherboard, which kicks in instead of your X800 when you reboot? If so, maybe there is a BIOS option to turn it off.

Or possibly, your X800 tries to use the DVI output instead of VGA or vice versa, don't know which one your monitor uses.[/QUOTE]Yes, my motherboard has onboard graphics but my monitor is hooked up to my PCI-e X800XL via VGA. I had to disable an onboard graphics setting in my BIOS when I installed the X800XL, but I will go through my BIOS again just to make sure I didn't miss anything that might be interfering with Linux. Anything in particular I should be looking for?

---

### Post by jdong on 2006-01-04
I'd like for you to go to bootdisk.com, and generate a MS-DOS boot CD or floppy (whichever is more convenient for you) and try to reboot from there (C-A-D -- DOS has no built-in reboot command), and see if the monitor turns off.

---

### Post by Trizik on 2006-01-04
There are many different bootdisks on that site. Does it matter which one I use?

---

### Post by jdong on 2006-01-04
no it doesn't... your goal is just to boot another OS to see how it handles, so we can tell if this is a Linux specific problem or something more that we need to work around with your hardware.

---

### Post by Trizik on 2006-01-04
OK, I will try that next, but let me just say that I am completely stumped because I've been booting into various "live CD" distros throughout the day and my results are quite different than the results I previously posted in this thread... and I haven't changed ANYTHING.

1) Booting off the SLAX live CD is never a problem, but rebooting after loading SLAX results in a sleeping monitor.

2) Sometimes the Feather Linux live CD boots just fine and I am able to reboot without experiencing the sleeping monitor! Other times the Feather Linux live CD halts with a bunch of errors and I am forced to reboot, which results in a sleeping monitor. The boot success rate seems very random.

3) Like Feather Linux, sometimes the DSL live CD boots fine and I am able to reboot without experiencing the sleeping monitor. But randomly at other times, the DSL live CD results in this error:> INIT: PANIC: segmentation violation at 0x804e19a! sleeping for 30 seconds.Rebooting after seeing this error results in a sleeping monitor.

I've also tried changing various video, power management, and other related settings in my BIOS, but haven't had any luck.

Let me just clear one thing up: When I say the monitor goes into sleep mode, I mean the power light turns orange, the screen displays "NO SIGNAL" for 3-5 seconds and then goes black.

I will try the MS-DOS boot disk now...

---

### Post by jdong on 2006-01-04
The segmentation violation and Feather symptoms seem to indicate CPU or RAM defectiveness. Can you run a memtest (on Ubuntu's boot menu, supposedly) for at least 30 minutes and report if any errors are found?

---

### Post by Trizik on 2006-01-04
I booted off a Windows 98 boot floppy... rebooted with C-A-D... monitor stayed on

I'll run a memtest now...

---

### Post by Trizik on 2006-01-05
memtest showed no errors

anything else i could try?

---

### Post by ysse on 2006-01-05
[QUOTE=Trizik]Yes, my motherboard has onboard graphics but my monitor is hooked up to my PCI-e X800XL via VGA. I had to disable an onboard graphics setting in my BIOS when I installed the X800XL, but I will go through my BIOS again just to make sure I didn't miss anything that might be interfering with Linux. Anything in particular I should be looking for?[/QUOTE]

Try connecting the monitor cable to the onboard VGA socket after your reboot. If you get signal there, then it is the onboard graphics that gets activated by Ubuntu. If not, fine, then we've ruled that possibility out.

---

### Post by Trizik on 2006-01-05
[QUOTE=ysse]Try connecting the monitor cable to the onboard VGA socket after your reboot. If you get signal there, then it is the onboard graphics that gets activated by Ubuntu. If not, fine, then we've ruled that possibility out.[/QUOTE]I booted into Ubuntu, rebooted the machine, unplugged the monitor from the PCI-e VGA when the screen displayed "NO SIGNAL" and then plugged the monitor into the onboard VGA, but the screen remained black. When I unplugged the monitor from the onboard VGA and plugged it back into the PCI-e VGA, "NO SIGNAL" appeared on the screen for a few seconds. So, there's definitely more activity coming from the PCI-e VGA than the onboard VGA.

---

### Post by jdong on 2006-01-05
[http://scottstuff.net/blog/articles/2005/03/17/msi-rs480m2-il-athlon-64-motherboard-mini-review](http://scottstuff.net/blog/articles/2005/03/17/msi-rs480m2-il-athlon-64-motherboard-mini-review)

A google for your mobo model + Linux reveals that you aren't the only person having trouble with this mobo and Linux. 


One thing out of that article that may be worth trying is "noapic", "nolapic" , or both as kernel arguments (like the reboot thing)

---

### Post by Trizik on 2006-01-05
I think his problem is a bit different than mine. His system is locking up, I don't think mine is. I just don't have video. Unless my system is locking up and that's why there's no video, but I would think at least something would appear, even the BIOS.

Also, if after losing video I shut my computer down for say 20 minutes without unplugging it from the wall socket, the monitor will still be sleeping when I boot it back up. If I shut it down again after that, the computer will automatically boot itself back up, and there still won't be any video. I have to completely kill the power to the power supply and drain the motherboard to get video back.

Is it possible that Linux is writing something in the CMOS (or somewhere else in the motherboard) that's disabling my monitor and that's why I have to drain the power from the motherboard to get video back?

---

### Post by juje on 2007-12-04
Ok, i have exactly de same problem, but without all the hardware knowledge...This is my story: i was working fine with my gutsy gibbon. I shut down my pc and remeber that i missed something in my mail...boot again and get some extreme screen configuration (i usually use something lis 1500x1000, or somethign like that, and it reboot like 2000x1500)..I thought my ubuntu hung up so i reboot...an then it happens...everything goes right until i loggin...my screen fall asleep but the cpu seems to keep on working...now i'm back to xp until i found a solution...any clue? I'm quit newbie in this hardware PC world so i would ask to teach as if i were quite a child...
Thanks!

My profile:

Ubuntu Gutsy Gibbon (clean install)
Mother asus p5ld2 se
intel core2duo e6420 lga775 pkg 2.13ghz
samsung syncmaster997mb
envidia geforce 7100 gs (pci)
tell me if its necessary any other info...

---

### Post by juje on 2007-12-04
Ok, i found a solution within this threat ([http://ubuntuforums.org/showthread.php?t=595032&highlight=monitor+blackout](http://ubuntuforums.org/showthread.php?t=595032&highlight=monitor+blackout)) ...i don't why my screen resolution change, but it work fine for me...

---


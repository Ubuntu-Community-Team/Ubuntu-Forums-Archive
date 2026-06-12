---
title: "Mouse and keyboard freezes after &quot;ata5: lost interrupt (Status 0x51)&quot;"
date: 2010-05-03
forum: Desktop Environments
---

### Post by israeldl on 2010-05-03
Hello everybody,

I've just update my computer to Ubuntu Lucid and I'm having some problems.

After a random time, my mouse and keyboard stop working and I get the following lines on dmesg (I have to get this using a ssh connection):

ata5: lost interrupt (Status 0x51)
[  980.000034] ata5.00: qc timeout (cmd 0xa0)
[  980.000046] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  980.000052] sr 5:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[  980.000066] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  980.000068]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[  980.000072] ata5.00: status: { DRDY ERR }
[  980.000097] ata5: soft resetting link
[  980.164344] ata5: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[  980.180257] ata5.00: configured for UDMA/66
[  985.180030] ata5.00: qc timeout (cmd 0xa0)
[  985.180037] ata5.00: TEST_UNIT_READY failed (err_mask=0x5)
[  985.180062] ata5: soft resetting link
[  985.348338] ata5: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[  985.360260] ata5.00: configured for UDMA/66
[  990.364027] ata5.00: qc timeout (cmd 0xa0)
[  990.364034] ata5.00: TEST_UNIT_READY failed (err_mask=0x5)
[  990.364040] ata5.00: limiting speed to UDMA/66:PIO3
[  990.364064] ata5: soft resetting link
[  990.524333] ata5: nv_mode_filter: 0x1f38f&0x1f39f->0x1f38f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[  990.544266] ata5.00: configured for UDMA/66
[  995.540030] ata5.00: qc timeout (cmd 0xa0)
[  995.540037] ata5.00: TEST_UNIT_READY failed (err_mask=0x5)
[  995.540041] ata5.00: disabled
[  995.540075] ata5: soft resetting link
[  995.696079] ata5: EH complete


Sometimes "ata5" is "ata1". 

Does anybody has an workaround?

---

### Post by candtalan on 2010-05-04
On a new 10.04 lucid install, I have been running for a day or so, the mouse and keyboard have just stopped responding. This happened immediately after logon. logon went ok so I guess the keyboard was getting through at that time. Mouse and kb are ps2.
I immediately also plugged in a usb mouse and it responded ok. However I dont have a usb keyboard to try or use.
I logged out and in but the problem stayed.
I restarted the PC and everything worked ok.
Any ideas?

---

### Post by d0pp on 2010-05-04
I have got the same problem. Didn't have the problem in 09.10. I got it after a fresh install of the 10.04-beta2. If I'm not able to fix this problem I see no other option than installing another distro. It's looks completely random when the crash appears.
I'm still able to ssh the computer after the mouse and keyboard freezes.
I should probably report a bug on this but I'm not quite sure how too. 

 -- In **/var/log/messages** this happens
May  4 21:13:54 desktop-linux kernel: [  258.040020] ata3: lost interrupt (Status 0x51)
May  4 21:13:59 desktop-linux kernel: [  263.040026] ata3.00: qc timeout (cmd 0xa0)
May  4 21:13:59 desktop-linux kernel: [  263.040038] sr 2:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  4 21:13:59 desktop-linux kernel: [  263.040072] ata3: soft resetting link
May  4 21:13:59 desktop-linux kernel: [  263.260235] ata3.00: configured for UDMA/33
May  4 21:14:04 desktop-linux kernel: [  268.260021] ata3.00: qc timeout (cmd 0xa0)
May  4 21:14:04 desktop-linux kernel: [  268.260028] ata3.00: TEST_UNIT_READY failed (err_mask=0x5)
May  4 21:14:04 desktop-linux kernel: [  268.260049] ata3: soft resetting link
May  4 21:14:05 desktop-linux kernel: [  268.480233] ata3.00: configured for UDMA/33
May  4 21:14:10 desktop-linux kernel: [  273.480022] ata3.00: qc timeout (cmd 0xa0)
May  4 21:14:10 desktop-linux kernel: [  273.480028] ata3.00: TEST_UNIT_READY failed (err_mask=0x5)
May  4 21:14:10 desktop-linux kernel: [  273.480032] ata3.00: limiting speed to UDMA/33:PIO3
May  4 21:14:10 desktop-linux kernel: [  273.480051] ata3: soft resetting link
May  4 21:14:10 desktop-linux kernel: [  273.700235] ata3.00: configured for UDMA/33
May  4 21:14:15 desktop-linux kernel: [  278.700023] ata3.00: qc timeout (cmd 0xa0)
May  4 21:14:15 desktop-linux kernel: [  278.700028] ata3.00: TEST_UNIT_READY failed (err_mask=0x5)
May  4 21:14:15 desktop-linux kernel: [  278.700031] ata3.00: disabled
May  4 21:14:15 desktop-linux kernel: [  278.700058] ata3: soft resetting link
May  4 21:14:15 desktop-linux kernel: [  278.860062] ata3: EH complete

**My hardware** (from lspci):

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:01.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:03.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
09:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
09:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

:confused:

---

### Post by candtalan on 2010-05-04
I have now purchased a usb keyboard so that if it happens again I can check to see if the usb keyboard will continue to work like the usb mouse does......

I know what you mean about having to leave Ubuntu, this can be a show stopper. I have not yet ever ssh'd into a frozen machine. If I have to to help with a bug I would try but just now it is outside my experience zone   :-(

Oh, I nearly forgot: This morning on this freezing machine, I lost the trash applet, and got freezing also. The forums message is

[http://ubuntuforums.org/showthread.php?t=1472161](http://ubuntuforums.org/showthread.php?t=1472161)
hope this can be useful  in some way?

---

### Post by israeldl on 2010-05-04
I still don't get it resolved.

My pc has nVidia video card too (the only thing I saw that we have in common). But I'm don't think this is the cause.

This is very stranger. I guess "ata3", "ata5" or "ata1" can be a HD or a cd drive, am I right? How is this affecting keyboard and mouse??? 

On Ubuntu 9.10 my pc works fine.

I've mailled this on Ubuntu mail list. If I get a answer, I post here.

---

### Post by d0pp on 2010-05-05
Just had a new crash.
Its all the same as the last one exept this time exept this time in was ata1

---

### Post by d0pp on 2010-05-06
Made a bug report on the problems.
[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344)

---

### Post by israeldl on 2010-05-08
> **d0pp said:**
> Made a bug report on the problems.
[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/113344)


[https://bugs.launchpad.net/ubuntu/+bug/576496](https://bugs.launchpad.net/ubuntu/+bug/576496)

---

### Post by israeldl on 2010-05-09
This thread have more people with our problem:
[http://ubuntuforums.org/showthread.php?t=1470452](http://ubuntuforums.org/showthread.php?t=1470452)

---

### Post by d0pp on 2010-05-11
Yesterday i installed the standard 32 bit version of Ubuntu 10.04, and haven't had any crashes yet. It's probably more of a workaround than a fix and since I'm having 4GB of ram maybe not 100% ideal. At least the kernel in the 32bit version supports PAE so this appears to be the best solution for me at the moment.

---

### Post by vek on 2010-05-30
This happens to me too (kind of) and I"m on the 32 bit version.

If you do a cat /proc/interrupts you might find that your mouse and keyboard are plugged into a hub that is sharing the same interurpt as your ATA driver (nvidia sata perhaps?).  For me its like this:
 23:     786792          0   IO-APIC-fasteoi   ohci_hcd:usb2, sata_nv

That OHCI_HCD appears to be a USB hub driver of some kind (I could be wrong?).  In my case, its the monitor I have the mouse and keyboard attached to.  Once I moved them away from that monitor into the other USB hub (ie, the actual one in my computer) they stopped freezing when the SATA driver barfed.  However, the SATA driver is still doing that, (I see it in the logs).  So I'm guessing if I were to plug stuff into those monitor ports it'd still be broken.

---

### Post by mario_7 on 2010-08-05
Also found this problem on my desktop PC upgraded form 9.10 to 10.04. It was happening only from time to time - sometimes after hours of running and sometimes few minutes after login. Hopefully the solution seems to be quite easy - updating the kernel to newer version (2.6.34):
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)
After about 2 days of (not too intensive) testing everything seems to be working fine. New kernel also fixed some issues with DVD-ROM not working properly before.

---


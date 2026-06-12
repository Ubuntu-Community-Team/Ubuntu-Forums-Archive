---
title: "Desktop Volume Control Problem"
date: 2005-07-30
forum: Desktop Environments
---

### Post by J1m on 2005-07-30
Hi Everyone,

Firstly, I'm brand new to Ubuntu and Gnome and so far I like it a lot.

However, I have a small problem.

I have a realtek AC97 (on board) sound chip which works fine, the thing is, the volume control on the desktop does not change the volume at all!!

I have been into the volume control preferences and I have tried both "Intel ICH5 (ALSA Mixer)" and "C-Media Electronics CMI9739 (OSS Mixer)"

Neither of them affect the volume of my sound (and I am sliding the master volume slider for each)

In the Multimedia Systems Selector panel only ALSA will play a test sound.  If I try to test OSS i get "Failed to construct test pipeline for 'OSS - Open Sound System'", however sound still works if I leave OSS selected! (even after reboot)

I've been through the unofficial ubuntu starter guide but my volume control still does not work.

I've installed the realtek AC97 linux drivers from realtek which made no difference - sound still works absolutely fine but the volume control still doesn't work.

Using alsamixer from the console does not change the volume.

Adjusting the volume slider on totem movie player does change the volume - but the desktop one just doesn't work.

If anyone can help, or point me in the right direction I'd appreciate it. I know it's not a huge problem but it's really pi**ing me off :)

jim@ubuntu:~$ lsmod | grep snd
snd_intel8x0           30400  1
snd_ac97_codec         73084  1 snd_intel8x0
snd_pcm_oss            47648  0
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                81416  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23428  1 snd_pcm
snd                    52228  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

Thanks in advance...

J1m

---

### Post by varunus on 2005-07-31
Did you follow the "configure sound properly" section of the UbuntuGuide?  This might help.

Strange, but my sound card (actual intel one, not a realtek one with the same chipset) works with the volume control.  I have to keep it on the ALSA mixer though.

---

### Post by J1m on 2005-07-31
Hi varanus.

Yes I followed the guide.

I really don't know what else I can try.

My ubuntu is fully up to date by the way, forgot to mention it before.

---

### Post by kassetra on 2005-08-01
[QUOTE=J1m]Hi varanus.

Yes I followed the guide.

I really don't know what else I can try.

My ubuntu is fully up to date by the way, forgot to mention it before.[/QUOTE]

Are you only adjusting the Master volume?  What about the PCM volume?  Master volume only works if PCM volume is not muted or turned down so low as to be off.

Also - have you tried using  ```
alsactl save
``` ?

---

### Post by heimo on 2005-08-01
[QUOTE=kassetra]
Also - have you tried using  ```
alsactl save
``` ?[/QUOTE]

alsactl store

(I make that mistake all the time.)

---

### Post by kassetra on 2005-08-01
[QUOTE=heimo]alsactl store

(I make that mistake all the time.)[/QUOTE]

oi!  I forget that every time - because of the "restore" option!

---

### Post by J1m on 2005-08-01
Hi kassetra.

I don't know!  I know I have tried adjusting the PCM slider bar - which didn't work - but I don't know if I did that with the Desktop Volume Control on ALSA and the Multimedia System Selector on ALSA as well.

So it's the PCM slider I need to adjust.  Or make sure it's on very low but not muted and then use the Master volume slider.

Ok I'll give it a try when I get home from work  :-P 

Cool thankyou.

---

### Post by Thomvis on 2005-08-01
I'm having exactly the same problem! I can't control my sound volume with alsa but other programs like cdplayer and rhythmbox can! 
Alsa is detecting the same cards as is the case with J1m. Also I cant use my mic, wich is quite irritating using Skype ;)
I followed the ubuntuguide and did the 'save' thing and tried to move every single bar in alsa.. but nothing works. I hope someone can help me/us!

Greetings, Thomas

---

### Post by agds on 2005-08-01
I was also frustrated by this problem for a while.  In my experience, the Master volume does absolutely nothing.

In order to control your volume from the gnome-panel Volume Control, you need to right click the speaker icon and select Preferences.  Then select either OSS or ALSA from the pull-down menu, depending on which one you're using, and select PCM from the scrolling list.  Click Close and you should now be able to control the volume without opening gnome-volume-control.

Now if I could just figure out how to make the keyboard shortcuts control the PCM volume as well…  Suggestions, anyone?

---

### Post by burlap on 2005-08-01
I had a lot of similar problems with via 8237 (c-media cmi9761). 

Final solution was to try out all possible devices (right click on volume control choose preferencese and set different devices) - one did work (something like "via dix" - this was not my machine, i dont remember). 

Strange thing is that master and pcm volume remains "blocked" (see [this screenshot](http://www.ubuntuforums.org/attachment.php?attachmentid=1597)). 

Hope this helps

---

### Post by agds on 2005-08-01
[QUOTE=Thomvis]I'm having exactly the same problem! I can't control my sound volume with alsa but other programs like cdplayer and rhythmbox can! 
Alsa is detecting the same cards as is the case with J1m. Also I cant use my mic, wich is quite irritating using Skype ;)
I followed the ubuntuguide and did the 'save' thing and tried to move every single bar in alsa.. but nothing works. I hope someone can help me/us!

Greetings, Thomas[/QUOTE]

For the mic issue, you may want to run gnome-volume-control and make sure the mic isn't muted or otherwise disabled.  It should appear in the Capture tab.  If it's not shown, you can make it visible from Edit -> Preferences.  You should also check to see that the ALSA mixer is selected.  This will be indicated by the title of the window.

---

### Post by Thomvis on 2005-08-02
:( it's not the solution. I allready tried every single slider in de alsa and oss mixer, gui and terminal (as if that makes difference ;)). 
Could it be that my soundcard isn't correctly installed because 'Return to the Castle of Wolfenstein' (to try 3d speed of linux) only works with sound disabled. Battle for Wesnoth is working fine though.. I really don't know where to search for the problem. 
Greetings, Thomas

edit/update: using Xine I discovered that I only can control the volume in Xine using the 'esd'. Is this information of any use to you?
update2: a message i'm getting often when starting a game: "open /dev/sequencer: No such file or directory" - sound works though.

---

### Post by J1m on 2005-08-02
Hi everyone,

I know my sound is using ALSA. I have set my Desktop Volume Controller to ALSA (right click > Preferences > IntelICH5(ALSA Mixer))  However the problem is...  there is no PCM to select from the list.

If I right click > Open Volume Control > Click on the Switches Tab I can uncheck PCM to mute sound or check it to have sound, however on the playback tab there is no slider bar.  If I now go to edit > preferences ...  If I untick PCM in this list, I no longer have the option to untick PCM on the switches tab.

Jeez does that make sense?

So my problem is I am actually missing the PCM slider bar!!

Anyone had this before?

---

### Post by agds on 2005-08-02
[QUOTE=Thomvis]edit/update: using Xine I discovered that I only can control the volume in Xine using the 'esd'. Is this information of any use to you?[/QUOTE]
If I understand correctly, the ESD control is the only way for you to adjust Xine's volume.  This may indicate that your Xine uses ESD for its output.  If your sound is configured according to Gandalf's HowTo (search for "esd" and "alsa," I think), Xine should use ALSA by default.  Maybe that helps…?

[QUOTE=J1m]If I right click > Open Volume Control > Click on the Switches Tab I can uncheck PCM to mute sound or check it to have sound, however on the playback tab there is no slider bar. If I now go to edit > preferences ... If I untick PCM in this list, I no longer have the option to untick PCM on the switches tab.[/QUOTE]
You may be encountering the same problem that burlap mentioned earlier in this thread.  Check out his screenshot.  Of course, it's a terminal window, but it looks like what you described.

---

### Post by Olav on 2005-08-03
Is not this problem due to reversed Master and Headphone channels? I am having exactly **that** problem right now, after reinstalling from scratch a few days ago, and I seem remember there was a solution for it. Only, I can not find back it too quickly... (will post here when I find it).

To see if you have the same problem, you may need to add the Headphone slider to the mixer through Preferences.

Symptoms are quite like yours: Master slider does not do anything, and neither do the hotkeys on my extended keyboard that I assigned to Volume up and Volume down. The Headphone slider OTOH, works.

No, I did not plug the speakers in the wrong port.

---

### Post by Thomvis on 2005-08-03
[QUOTE=agds]If I understand correctly, the ESD control is the only way for you to adjust Xine's volume.  This may indicate that your Xine uses ESD for its output.  If your sound is configured according to Gandalf's HowTo (search for "esd" and "alsa," I think), Xine should use ALSA by default.  Maybe that helps…?
[/QUOTE]
The thing is: when I configure Xine using ALSA for sound output, the Xine volume control isn't working. When I set ESD to output, after a restart of Xine, the sound control (in Xine) is working.

I walked through a similar howto as Gandalfs but later today I'll try this HOWTO too. Thanks for the suggestions! I hope we'll sort it out,

Greetings, Thomas

---

### Post by Thomvis on 2005-08-03
I followed the HOWTO by gandalf but it didn't make any difference. Using beep media player I can only ajust the sound using software-control(don't know the exact name, I use dutch ubuntu). I looks like my card is not found properly and no hardware control is possible. That explains a lot of trouble, but how to fix it..

Greetings,
Thomas

---

### Post by agds on 2005-08-03
If Ubuntu isn't detecting your sound card properly, you might want to check /var/log/dmesg for anything unusual.  I'm afraid I don't know enough to advise you beyond that.

---

### Post by Thomvis on 2005-08-04
I couldn't find a clue in the dmesg, but that can be me.. so here's my dmesg output:
```
n type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12 14 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
pnp: 00:0a: ioport range 0x400-0x4bf could not be reserved
audit: initializing netlink socket (disabled)
audit(1123151916.801:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
SLPB PCI0 HUB0 UAR1 USB0 USB1 USB2 USB3 USBE MODM
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: Fan [FAN] (on)
ACPI: Thermal Zone [THRM] (40 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH5: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH5: chipset revision 2
ICH5: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
    ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: ST3200021A, ATA DISK drive
hdb: IDE DVD-ROM 16X, ATAPI CD/DVD-ROM drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 1024KiB
hda: 390721968 sectors (200049 MB) w/2048KiB Cache, CHS=24321/255/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 >
Probing IDE interface ide1...
hdc: PIONEER DVD RW DVR-107D, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
hdb: ATAPI 48X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ts: Compaq touchscreen protocol output
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
ndiswrapper: using irq 16
wlan0: ndiswrapper ethernet device 00:60:b3:a3:66:dd using driver prisma00
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ndiswrapper: driver prisma00 (GlobespanVirata,12/05/2003, 2.1.14.2) added
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
NTFS volume version 3.1.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 865 Chipset.
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xe0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0xcc00
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xc000
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xc400
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
usb 1-1: new low speed USB device using uhci_hcd and address 2
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0xc800
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xfa800000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
usb 1-2: new low speed USB device using uhci_hcd and address 3
usbcore: registered new driver hiddev
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usbhid: probe of 1-1:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
hw_random: RNG not detected
usb 1-1: USB disconnect, address 2
usb 5-3: new high speed USB device using ehci_hcd and address 4
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
intel8x0_measure_ac97_clock: measured 49097 usecs
intel8x0: clocking to 48000
usb 1-1: new low speed USB device using uhci_hcd and address 4
Loaded prism54 driver, version 1.2
Linux video capture interface: v1.00
input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.0-1
saa7130/34: v4l2 driver version 0.2.12 loaded
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 18
saa7134[0]: found at 0000:02:02.0, rev: 1, irq: 18, latency: 32, mmio: 0xfa402000
saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
saa7134[0]: board init: gpio is 0
usb 1-2: new low speed USB device using uhci_hcd and address 5
saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner: chip found at addr 0xc0 i2c-bus saa7134[0]
tuner: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3)) by saa7134[0]
tda9885/6/7: chip found @ 0x86
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
saa7134[0]: registered device radio0
via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
ACPI: PCI interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 20
eth0: VIA Rhine III at 0xb000, 00:0c:76:a5:3f:61, IRQ 20.
eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
input: USB HID v1.10 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-2
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
input,hiddev96: USB HID v1.10 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-2
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fa404000-fa4047ff]  Max Packet=[2048]
input: USB HID v1.10 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-2
usb 2-2: new full speed USB device using uhci_hcd and address 2
usb 2-2: device descriptor read/64, error -75
usb 2-2: unable to read config index 0 descriptor/all
usb 2-2: can't read configurations, error -75
usb 2-2: new full speed USB device using uhci_hcd and address 3
usb 2-2: unable to read config index 0 descriptor/all
usb 2-2: can't read configurations, error -75
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000520e83]
  Vendor: Generic   Model: CF Card       CF  Rev: 1.3B
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: MS Card       MS  Rev: 1.3B
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: SD Card   MMC/SD  Rev: 1.3B
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: SM/XD Card    SM  Rev: 1.3B
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1
Attached scsi removable disk sdc at scsi0, channel 0, id 0, lun 2
Attached scsi removable disk sdd at scsi0, channel 0, id 0, lun 3
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 122679296
[fglrx] max   LFB = 122679296
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-input.c: event field not found
drivers/usb/input/hid-core.c: input irq status -84 received
wlan0: no IPv6 routers present
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
mtrr: no MTRR for e8000000,400000 found
mtrr: no MTRR for e8400000,100000 found
mtrr: no MTRR for e8500000,1000 found
[fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 122679296
[fglrx] max   LFB = 122679296
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'MUSE HULLABALOO DISC2', timestamp 2036/02/07 03:58 (1078)
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'MUSE HULLABALOO DISC1', timestamp 2036/02/07 03:58 (1078)
hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
hdb: cdrom_decode_status: error=0x40LastFailedSense 0x04
hdb: CHECK for good STATUS
```

Thank you for your help! I hope somebody else can help me,
Greetings Thomas

---

### Post by phen on 2005-08-29
just a quick note: i am using an intel ich whatever soundchip, and my vol control works perfectly. is use "analog devices ad1981 (OSS)" for gnome volume control, and ESD in beep media player, xine, totem and so on. Maybe that does help you!

another thing i just discovered:

sometimes, i had problems with the beep sound control. it did work, but there was only little difference between 0% and 100%, and sometimes it didn't work at all. now, i ticked beep->settings->output->esd output>settings>volume slider controls ossmixer, and everything's working fine :-)

---

### Post by jam02 on 2006-09-02
my solution was to right click on the sound icon, and set the device back to my sound card, and not my camera o.O
I started getting the porblem after coming out of hibination.

---


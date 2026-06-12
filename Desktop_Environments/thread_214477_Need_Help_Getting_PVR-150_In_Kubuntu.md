---
title: "Need Help Getting PVR-150 In Kubuntu"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Rock on 2006-07-12
I can't get it to work in tvtime or mythtv and I can't cap with the cap command either. Tvtime says the device or resource is busy. Cap command gives me 0B for the file size and mythtv just gives me a black picture and freezes up the program. this is what dmesg gives me.
> [4294687.785000] ivtv:  ==================== START INIT IVTV ===================
=
[4294687.785000] ivtv:  version 0.4.6 (tagged release) loading
[4294687.785000] ivtv:  Linux version: 2.6.15-23-686 SMP preempt 686 gcc-4.0
[4294687.785000] ivtv:  In case of problems please include the debug info betwee
n
[4294687.785000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294687.785000] ivtv:  any module options, when mailing the ivtv-users mailingl
ist.
[4294687.785000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294687.785000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 20 (level, low) -> I
RQ 177
[4294687.785000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294687.806000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294687.847000] Linux agpgart interface v0.101 (c) Dave Jones
[4294687.850000] agpgart: Detected AGP bridge 0
[4294687.854000] agpgart: AGP aperture is 128M @ 0xd8000000
[4294687.906000] tveeprom: ivtv version
[4294687.906000] tveeprom: Hauppauge: model = 26582, rev = F0B2, serial# = 94939
43
[4294687.906000] tveeprom: tuner = TCL M2523_5N_E (idx = 112, type = 50)
[4294687.906000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000
)
[4294687.906000] tveeprom: audio processor = CX25843 (type = 25)
[4294687.906000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294687.906000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294687.933000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #
0
[4294687.933000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294688.079000] cx25840 0-0044: ivtv driver
[4294688.079000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294691.007000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer de
v 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8604
[4294691.008000] usbcore: registered new driver usblp
[4294691.008000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driv
er
[4294691.036000] input: PC Speaker as /class/input/input1
[4294691.234000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[4294691.340000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294691.393000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294691.439000] parport: PnPBIOS parport detected.
[4294691.439000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294691.464000] Floppy drive(s): fd0 is 1.44M
[4294691.480000] FDC 0 is a post-1991 82077
[4294691.515000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294691.522000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294691.798000] ts: Compaq touchscreen protocol output
[4294692.236000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294692.456000] ivtv0: Encoder revision: 0x02050032
[4294692.457000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4
096KB total)
[4294692.457000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20
48KB total)
[4294692.457000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20
48KB total)
[4294692.457000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer
s (2048KB total)
[4294692.458000] tuner: type set to 50 (TCL 2002N) by ivtv i2c driver #0
[4294692.531000] ivtv0: Initialized WinTV PVR 150, card #0
[4294692.531000] ivtv:  ====================  END INIT IVTV  ===================

---

### Post by metalheart on 2006-07-12
tvtime does not support mpeg cards (according to their web page).

---

### Post by Rock on 2006-07-12
Ok but how about mythtv? my old card (ati tv wonder pro) worked fine in it expect it only had  sound on the left speaker

---

### Post by metalheart on 2006-07-12
What I can recommend is to follow the mythtv how-to for Ubuntu
[http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv]("http://www.ubuntuforums.org/showthread.php?t=186747&highlight=mythtv")

---

### Post by Rock on 2006-07-13
Perfect. Thanks, now I just need my remote contrl and IR Blaster (for my digital cable box) working.

---

### Post by Rock on 2006-08-13
Still need IR Blaster working. Help would really be  appreciated.

---


---
title: "DVD problems"
date: 2005-05-30
forum: Desktop Environments
---

### Post by danip on 2005-05-30
If I watch a dvd on my laptop I have a problem witht he playback.  It is very sluggish and the video seems to do a sort of freeze then play skipping thing.  It's almost as if either my computer is not fast enough or the dvd drive is not fast enough.  I know this is not the case because I have never had this problem with other operating systems.  I am running a p4 2.8ghz 512 ram.  The video card is a 32mb onboard intel graphics card.

---

### Post by Takis on 2005-06-02
Sounds like DMA needs to be turned on.
[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

---

### Post by jdgiotta on 2005-11-07
Allot of threads all come to the same suggestion, by setting the drive to DMA "on".
However, this still won't fix my problem. I've set the hparm.conf and I still get jerky playback.

---

### Post by Takis on 2005-11-07
What kind of computer (hardware) are you running? Is it intuitively enough to play DVDs?

---

### Post by jdgiotta on 2005-11-08
Hey Takis,
The ran Windows XP Pro without any DVD problems.

It's a HP Pavilion ze4610us (laptop)
[LIST]
[*]Mobile AMD Athlon XP-M Processor 2500+
[*]512 DDR SDRAM
[/LIST]

---

### Post by jdgiotta on 2005-11-10
I finally got my playback to work properly.
I was shopping around for a Totem replacement and I installed VLC, but whatever packages or package fixes that came bundled in VLC corrected my playback in Totem.

I haven't needed to use VLC because everthing is working fine in Totem now.

---

### Post by Takis on 2005-11-10
Trippy. Don't you just hate it when things like that happen...?

---

### Post by dninja on 2005-12-07
I'm also getting jerky dvd playback in totem but not all the time and occasionally the sound is  delayed by a second or so.

Just in case I also tried installing vlc but that plays up worse than totem

I've tried searching for the HDIO error mentiaoned in the outputs below and I've seen it mentioned quite a bit but with no solutions offered.

I have dma turned on and a good enough spec pc. The info below may help somene diagnose the problem:

timing
```

hdparm   -tT /dev/hdc

/dev/hdc:
 Timing cached reads:   1292 MB in  2.00 seconds = 645.13 MB/sec
 Timing buffered disk reads:   12 MB in  3.53 seconds =   3.40 MB/sec

```

hdparam output
```

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

lspci
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```
cat /proc/cpuinfo
```

processor   : 0
vendor_id   : AuthenticAMD
cpu family  : 6
model       : 8     
model name  : AMD Athlon(tm) XP 2600+
stepping    : 1
cpu MHz     : 2075.452
cache size  : 256 KB
fdiv_bug    : no    
hlt_bug     : no    
f00f_bug    : no    
coma_bug    : no    
fpu     : yes   
fpu_exception   : yes   
cpuid level : 1
wp      : yes   
flags       : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips    : 4104.19 

```

modules
```

lsmod | grep ide
video                  16004  0
ide_cd                 36996  1
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  9
ide_generic             1664  0
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx

```


EDIT - Just noticed that this thread was for Hoary, my problem is on Breezy so I'm going to post the mail there instead.

---

### Post by jdgiotta on 2005-12-08
I was never able to get VLC to work, but when I did install it Totem started to work fine.

---

### Post by dninja on 2005-12-08
I managed to fix it. I installed totem-xine which removed gstreamer. All is happy now with totem, I haven't bothered trying vlc again.

---


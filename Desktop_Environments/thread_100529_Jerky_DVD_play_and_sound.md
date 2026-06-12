---
title: "Jerky DVD play and sound"
date: 2005-12-07
forum: Desktop Environments
---

### Post by dninja on 2005-12-07
I originally posted this to a thread in Hoary but as I'm actually using breezy I've edited that one and am posting this here.

There is a lot of talk on Hoary about jerky dvd playback but not much on Breezy, hopefully this means that my problem will have an easy solution.

'm getting jerky dvd playback in totem, not all the time and occasionally the sound is  delayed by a second or so.

I saw another post saying that installing vlc for some reason fixed his so I also tried installing it but it plays up worse than totem

I've tried searching for the HDIO error mentiaoned in the outputs below and I've seen it mentioned quite a bit but with no solutions offered.

I have dma turned on and a good enough spec pc. The info below may help somone diagnose the problem:

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

I feel reluctant posting this here as there are similar discussions on hoary but as it is a breezy install this seems like the right place to put this.

---

### Post by teaker1s on 2005-12-07
I faired better with okle totem not good for me

---

### Post by WebDrake on 2005-12-07
Interesting; I haven't tried DVD playback, but I get very jerky CD audio playback on my Breezy system.  I can't compare to Hoary because this is the first time I've had Linux on my machine.

Out of curiosity, what DVD drive are you using?  Mine is a Nec DVD+RW 6100A.  Perhaps it's a driver issue?

---

### Post by soulestream on 2005-12-07
everything i could think of you checked. I would however, ask what apps/services you are running during the playback. Also make sure the dvd is clean. The drive and the disc. 

I use Mplayer and have no issues on any of my systems

soule

---

### Post by dninja on 2005-12-07
I love posting here as I usually fix things just after posting. I installed totem-xine which removed gstreamer and that seems to have fixed everything.

I would still like to know what the error
```

 HDIO_GETGEO failed: Invalid argument

```
means though

---


---
title: "Parallel port support"
date: 2009-01-28
forum: General Help
---

### Post by ashen on 2009-01-28
Hi,

I have just added a PCI parallel port card to my computer and am having difficulties getting ubuntu to recognise it ...

I am running Ubuntu 8.10 with the 2.6.27-9-generic kernel.

I have added a brainboxes uc-146 card (since on the data sheet it said it was compatible with linux) and am very confused with what i'm supposed to do to make ubuntu see it.  The parport, parport_pc, and ppdev modules are all loaded, but there is no parport0 or lp0 in /dev/.

When I contacted the company they sent me some information about getting their serial cards working - is all this applicable to getting the parallel port working?  I tried following their instructions to use setserial, but this didn't work.

The output of ```
lspci -vv
``` is:

```

07:00.0 Parallel controller: Brain Boxes Device 0be2 (rev 01) (prog-if 01)
	Subsystem: Brain Boxes Device 0000
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at e3001000 (32-bit, non-prefetchable) [size=128]
	Region 1: I/O ports at 1000 [size=128]
	Region 2: I/O ports at 1080 [size=64]
	Region 3: I/O ports at 10c0 [size=16]
	Region 4: Memory at e3001080 (32-bit, non-prefetchable) [size=64]
	Region 5: Memory at e30010c0 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

```

so it seems that the card is installed ok - but how do i use it?

Thanks for any help you can provide!

Alex

---

### Post by ashen on 2009-01-28
Answering my own question somewhat ...

I have to remove the lp and parport_pc modules

```

$ sudo rmmod lp
$ sudo rmmod parport_pc

```

and then reload parport_pc with the i/o address* and no irq

```

$ sudo /sbin/insmod /lib/modules/2.6.27-9-generic/kernel/drivers/parport/parport_pc.ko io=0x10c0 irq=none

```

then reload lp

```

$ sudo /sbin/insmod /lib/modules/2.6.27-9-generic/kernel/drivers/char/lp.ko

```

which gives:

```

$ lsmod
Module                  Size  Used by
lp                     17156  0 
parport_pc             39204  1 
af_packet              25728  0 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxnetflt             92040  0 
vboxdrv               118824  1 vboxnetflt
ppdev                  15620  0 
parport                42604  3 lp,parport_pc,ppdev
ipv6                  263972  16 
acpi_cpufreq           15500  0 
cpufreq_stats          13188  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  4 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
evdev                  17696  8 
intel_agp              33724  0 
iTCO_wdt               18596  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               6909268  36 
agpgart                42184  2 intel_agp,nvidia
i2c_core               31892  1 nvidia
psmouse                45200  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
pcspkr                 10624  0 
serio_raw              13444  0 
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
heci                   65936  0 
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_piix               24580  3 
usbhid                 35840  0 
hid                    50560  1 usbhid
pata_acpi              12160  0 
ohci1394               37936  0 
pata_marvell           11776  0 
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
ata_generic            12932  0 
uhci_hcd               30736  0 
usbcore               148848  4 usbhid,ehci_hcd,uhci_hcd
e1000e                112680  0 
libata                177312  4 ata_piix,pata_acpi,pata_marvell,ata_generic
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

(I found this just by fiddling around with removing/reloading modules...)

Now i just need to find out how to have all this done automatically on boot - any ideas?

Cheers,

Alex

* this i/o address is the i/o address for region 3 of the parallel controller (since apparently this region corresponds to the parallel registers)

---

### Post by ashen on 2009-01-30
**SOLVED!**

And now I've totally solved my problem :)

the options for parport_pc go in the /etc/modprobe.d/options file

i.e.

```

# enable parport_pc with the correct parameters
options parport_pc io=0x10c0 irq=none

```

and then I made sure to load parport_pc before lp in my /etc/modules file

i.e.

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
sbp2
parport_pc
lp

```

Now my computer boots with parallel port support enabled!

I was confused by the information on the internet that used modules.conf to set options,for the kernel modules.

Hope this helps other people!

Alex

---

### Post by Mesanna on 2009-07-23
Alex, just wanted to say that you're my hero of the month :D

I bought a parallel port card as my new motherboard didn't have one and the USB port on my printer stopped working after my young nephew "played" with it one day!

The documentation from the card manufacturer was less than helpful, but I followed your instructions and now have a working printer. It didn't work first time, because I was copying your commands, instead of actually reading what you'd written, and I didn't change the I/O address to the setting for my particular machine, but that was entirely my stupid fault! Once I changed the I/O from 10c0 to bd00 (my region), I restarted and it worked perfectly! I'm not sure I would ever have figured this out on my own, so thanks ever so much!

---

### Post by ashen on 2009-08-04
So glad it helped you!

Like in your case, the documentation from the manufacturer was practically useless.  I contacted them and they told me the closest they had to support for me was some drivers for a (very) old version of the kernel!

Fortunately the internet is awesome! :)

Alex

---


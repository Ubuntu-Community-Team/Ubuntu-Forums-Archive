---
title: "GeForce 9600 gso not recognized under Ubuntu 8.10"
date: 2008-12-14
forum: Gaming &amp; Leisure
---

### Post by mikemosher on 2008-12-14
Hello, 

I just bought a Dell Vostro 200, and I purchased a separate Nvidia GeForce 9600 GSO graphics card.  I installed Ubuntu 8.10, and I installed the graphics card myself.  

Once I booted up, It doesn't even see the graphics card.   I try to run NVIDIA-Linux-x86_64-171.06.01-pkg0.run (from nvidia), and it says  I don't have an nvidia card.  

I put the card in the PCI slot, and I figured that Linux would at least be able to recognize it.   

here's a cat of lspci and lsmod:


lspci:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)



lsmod:
Module                  Size  Used by
ipv6                  314312  14 
af_packet              29568  2 
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
acpi_cpufreq           16400  0 
cpufreq_ondemand       16400  2 
cpufreq_conservative    16392  0 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
cpufreq_userspace      12420  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
wmi                    15808  0 
video                  28948  0 
output                 11776  1 video
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
container              12288  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
saa7134_alsa           22432  0 
saa7134               171228  1 saa7134_alsa
ir_common              51716  1 saa7134
compat_ioctl32         18176  1 saa7134
videodev               46720  2 saa7134,compat_ioctl32
v4l1_compat            24580  1 videodev
v4l2_common            21888  1 saa7134
dcdbas                 16688  0 
videobuf_dma_sg        22788  2 saa7134_alsa,saa7134
serio_raw              14596  0 
videobuf_core          29956  2 saa7134,videobuf_dma_sg
psmouse                51612  0 
tveeprom               23428  1 saa7134
pcspkr                 11136  0 
i2c_core               36128  3 saa7134,v4l2_common,tveeprom
iTCO_wdt               21072  0 
iTCO_vendor_support    12420  1 iTCO_wdt
evdev                  20512  6 
snd_hda_intel         489264  2 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
shpchp                 42140  0 
button                 15904  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
intel_agp              39280  1 
pci_hotplug            39472  1 shpchp
ext3                  150544  2 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
usbhid                 39776  0 
hid                    59072  1 usbhid
ata_piix               29444  3 
pata_acpi              13568  0 
ata_generic            14212  0 
libata                200160  3 ata_piix,pata_acpi,ata_generic
scsi_mod              183160  4 sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
uhci_hcd               34336  0 
ehci_hcd               48908  0 
usbcore               175376  4 usbhid,uhci_hcd,ehci_hcd
e1000e                128680  0 
thermal                27424  0 
processor              47800  2 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 
compcache              13808  1 
lzo_decompress         11264  1 compcache
lzo_compress           11264  1 compcache
tlsf                   15392  1 compcache



Any ideas as to why it isn't recognizing my card, and why I can't install the drivers? 
 
PS - on a side note, the manual for the card said that I could get 'improved performance' by plugging in a 6-hole power cord coming from the power supply into the card.   The tower does not have any more plugs coming from the power supply (all used).   this isn't the only power provided to the card, right?  Just thinking of why the card isn't even recognized under lspci...


thanks in advance.

---

### Post by sirdilznik on 2008-12-14
That card was likely unsupported in that driver version.  Why are you installing such an early driver version and why are you manually installing the driver?  Why not just install nvidia-glx-177 from the repos.  I can tell you for a fact that it supports the 9600 GSO.

---

### Post by mikemosher on 2008-12-14
Thanks for the reply.   I tried installing that from the repos, rebooting, and nothing happened.   

I still can't see the hardware.  Any ideas why it isn't showing up?

---

### Post by Vadi on 2008-12-14
Only the driver that came out a few days ago supports your card. See here for information: [http://www.phoronix.com/scan.php?page=article&item=nvidia_18016&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_18016&num=1)

---

### Post by mikemosher on 2008-12-14
I looked on the link you added, and I don't see my card in the list.   The card I have is a GeForce 9600 GSO.   I tried to install the driver, and again it told me that it can't find the card.   

I've verified that the card is in the slot correctly, and I see the fan working and lights are going.   I assume since the card has power, the OS could see it. It's not showing up on 'lspci' (which I think is the 1st problem before trying to work out the correct driver...)


Thanks again.

---

### Post by Vadi on 2008-12-14
Oh :(. I'm not a hardware expert unfortunately, but the guys here: [http://www.phoronix.com/forums/](http://www.phoronix.com/forums/) are, I'd recommend cross-posting to that forum.

---

### Post by mikemosher on 2008-12-14
Thanks for the link.  I'll be looking around that forum as well.  

Anyone else here know what I could do to test if Linux sees the card, what I can do to get it to recognize the card, or any other help?  

thanks again to all.

---

### Post by farrell2k on 2008-12-14
I have the 9600gso 384mb version and I can tell you without a doubt that you do not want to install the 1.77x drivers.  I have been using them for 3 days and I have noticed speed decreases of 2x. glxgears usually gives me 10k, but with 1.77x I was getting 5k.  You need to install the 1.80 beta drivers from nvidia.  The problem has been resolved.   Do the manual install it isn't hard.

---

### Post by mikemosher on 2008-12-14
It's good to know that the 180 driver worked for someone else with this card, but once again, these drivers tell me that it can't find an nvidia card on my machine.  I also don't find it listed under 'lspci'.  

Does anyone know why linux doesn't recognize my card at all??  

thanks...

---

### Post by mikemosher on 2008-12-14
Thanks for all the responses guys.  

It looks like my issue is due to the fact that I don't have a powerplug connected to the card.  That's why the OS couldn't see it.  I never received one in the box with the card, so I have to look for one tomorrow... 

Again, thanks for the responses.

---

### Post by mikedep333 on 2008-12-14
I have a 9600 GSO too. It works fine with the proprietary driver that "hardware drivers" suggests. You need a 2x molex to PCI-Express power adapter.
[IMG]http://www.playtool.com/pages/psuconnectors/pcie6.jpg[/IMG]

Also, the Geforce 9600 GSO is rated for using 105 watts of power maximum. Your power supply is only 300W. It may be that you need to step down to the 50W 9500GT, which does not even require a pci-e power connector. (the 9600GT is 98W so it isn't much different from your GSO.)
[http://en.wikipedia.org/wiki/GeForce_9_Series](http://en.wikipedia.org/wiki/GeForce_9_Series)

If indeed your 9600 GSO does work, do not add a 2nd hard drive or optical drive or anything like that which would use a lot more power.

---

### Post by Vadi on 2008-12-15
Glad you got it working :)

---


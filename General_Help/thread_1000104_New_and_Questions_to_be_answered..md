---
title: "New and Questions to be answered."
date: 2008-12-02
forum: General Help
---

### Post by Grolsche on 2008-12-02
Hi,

I am new to the world of linux and especially Ubuntu. I have installed Ubuntu on my system in a different partition to windows so I can test and play with Ubuntu until I am happy to swap over 100%.

However, being new to Ubuntu and Linux I have a few questiosn which may sound noobish but would definately would appreciate your help.

With Ubuntu installed. Like with Windows you normally have to install motherboard drivers and so on. My first question is Do I need to install motherboard drivers with Ubuntu so to make the agp slot etc work properly?

If so, where can I get the drivers for the motherboard? I have tried looking on my motherboard manufacturers website and they only provide drivers for windows.

The next question would also be how do I install drivers and how do I know if they are successfully installed?

Aplogies for these questions but being so use to windows installations and how it mainly uses graphical interfaces and practically does all this work for you, I have no idea on what to do when it comes to this bit with linux.

I hope you can help me and guide me successfully in to this new world.

---

### Post by oilchangeguy on 2008-12-02
> **Grolsche said:**
> Hi,

I am new to the world of linux and especially Ubuntu. I have installed Ubuntu on my system in a different partition to windows so I can test and play with Ubuntu until I am happy to swap over 100%.

However, being new to Ubuntu and Linux I have a few questiosn which may sound noobish but would definately would appreciate your help.

With Ubuntu installed. Like with Windows you normally have to install motherboard drivers and so on. My first question is Do I need to install motherboard drivers with Ubuntu so to make the agp slot etc work properly?

If so, where can I get the drivers for the motherboard? I have tried looking on my motherboard manufacturers website and they only provide drivers for windows.

The next question would also be how do I install drivers and how do I know if they are successfully installed?

Aplogies for these questions but being so use to windows installations and how it mainly uses graphical interfaces and practically does all this work for you, I have no idea on what to do when it comes to this bit with linux.

I hope you can help me and guide me successfully in to this new world.


in regard to ubuntu drivers, if you've already installed ubuntu, the only thing you need it do is to ask yourself is everything on my computer working? if it is then you've answered your question about drivers. if it's not, it's most likely not a driver issue. if you're having problems with a certain device, post back about the device.

---

### Post by Grolsche on 2008-12-02
Hi Everything appears to be working fine. But how do I know if it is? I do have an ATI Radeon 9250 graphics card which I know isn't using its full 3d capability, which might be the reason the system seems slightly slower than expected.

I am not sure how I can tell what graphic driver its working with and how to go about updating it with a new one.

I did try the x.org ati driver but that made the system have a few problems and once i worked out how to uninstall it, the system booted fine again.

---

### Post by philinux on 2008-12-02
What driver is offered when you open System>Admin>Hardware Drivers

---

### Post by Grolsche on 2008-12-02
I did try that but it came up with nothing in it.

---

### Post by 2hot6ft2 on 2008-12-02
If hardware drivers didn't find anything then try Applications>System Tools>EnvyNG

I'm kinda surprised that Hardware Drivers doesn't show a driver for it. If EnvyNG isn't in System Tools then System>Administration>Synaptic Package Manager and search for envyng and mark it for installation and install it by hitting apply.

---

### Post by HermanAB on 2008-12-02
Linux is much easier to install than Windows and will usually configure all your hardware for you without any effort on your part.

Here are some spy commands to see what is going on:

$ sudo lsmod
$ sudo lspci

Cheers,

Herman

---

### Post by Grolsche on 2008-12-03
> **2hot6ft2 said:**
> If hardware drivers didn't find anything then try Applications>System Tools>EnvyNG

I'm kinda surprised that Hardware Drivers doesn't show a driver for it. If EnvyNG isn't in System Tools then System>Administration>Synaptic Package Manager and search for envyng and mark it for installation and install it by hitting apply.

Okay i tried this and got envy up but I dont really know what i'm doing with this. It lists an ATI Driver and some Nvidia drivers and says non are compatible????

I did last night look on the ATI website again and did read the installation instructions but it said i would need the following:

# POSIX Shared Memory (/dev/shm) support is required for 3D apps
# glibc version 2.2 or 2.3
# Linux kernel 2.4 or higher
# XOrg 6.7,6.8,6.9,7.0 or 7.1; XFree86 version 4.3 

Now not knowing much about linux or Ubuntu do i need any of these are all of these already installed and if I do need them where do I get them from?

---

### Post by Grolsche on 2008-12-03
> **HermanAB said:**
> Linux is much easier to install than Windows and will usually configure all your hardware for you without any effort on your part.

Here are some spy commands to see what is going on:

$ sudo lsmod
$ sudo lspci

Cheers,

Herman

If i try any of those commands it comes up with command not found.

incase it helps I am using release 8.10

---

### Post by Nathan Sweeney on 2008-12-03
> **Grolsche said:**
> If i try any of those commands it comes up with command not found.

incase it helps I am using release 8.10

Really?  Are you typing just the "sudo lspci" or "sudo lsmod" part?  The $ is just how Herman is representing the command prompt.

---

### Post by Grolsche on 2008-12-03
> **Nathan Sweeney said:**
> Really?  Are you typing just the "sudo lspci" or "sudo lsmod" part?  The $ is just how Herman is representing the command prompt.

Yes I did understand not to put the $ and I did type it without the $ and got that message.

---

### Post by Grolsche on 2008-12-03
ok guys, sorry about the misunderstanding. it seems i had the misinterpreted the l as an i :). the commands did work and this is what I got.

Module                  Size  Used by
ipv6                  263972  10 
isofs                  40100  0 
udf                    88356  1 
crc_itu_t              10112  1 udf
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
wmi                    14504  0 
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
video                  25104  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
evdev                  17696  8 
snd_intel8x0           37532  4 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
asix                   22656  0 
usbnet                 24072  1 asix
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
mii                    13440  2 asix,usbnet
psmouse                45200  0 
serio_raw              13444  0 
snd_seq_dummy          10884  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
pcspkr                 10624  0 
snd                    63268  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
intel_agp              33724  1 
agpgart                42184  1 intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
sd_mod                 42264  7 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  6 
ata_generic            12932  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
skge                   48144  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 asix,usbnet,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  9 
alan@Main-Desktop:~$ sudo ispci
sudo: ispci: command not found
alan@Main-Desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

So by the looks of it most things are setup ok. 

Just now need to get the driver installed so it can use 3d properly.

---


---
title: "Compiz-Fusion Help in Gutsy"
date: 2007-11-23
forum: Desktop Effects &amp; Customization
---

### Post by amtur_poet on 2007-11-23
I just recently upgraded from Ubuntu 7.04 to 7.10, because I was eager to use compiz-fusion. However, when I was done upgrading, and I booted into Gutsy, there was not trace of compiz on the system. [My computer also had a horrible MBR crash afterwards, but I don't know if those 2 occurances are related.] I was able to fix my system, and re-install Ubuntu 7.04. I'm worried that if I upgrade, my computer will crash again, and I can't get compiz-fusion to install on 7.04, because I'm a linux beginner, and don't know much about code installation. Can someone help me with either one of these problems?

---

### Post by bluepowder7 on 2007-11-23
1 - i found that a fresh install of 7.10 is much better than an upgrade from 7.04, so maybe try that approach

2 - once you have 7.10, fusion is there but the fancy manager for it isn't installed, so you'd need to install it through synaptic.  it's very much point-n-click to do that.  very easy.

---

### Post by Cragrat on 2007-11-23
Sorry, what's the fancy manager actually called?

---

### Post by bluepowder7 on 2007-11-23
> **Cragrat said:**
> Sorry, what's the fancy manager actually called?

if you go to Synaptic, look for "compizconfig-settings-manager" and check it for installation.  it might have to download and install some other bits as well, so just OK those.

once it's installed, it'll show up under System - Preferences - Advanced Desktop Effects Settings

---

### Post by Cragrat on 2007-11-23
Thanks. I think I have this now. When I right click the desktop and go to 'Change Desktop Background', on the Visual Effects Tab, I can't select anything other than 'Normal'.
I can see the Compiz-Fusion in Preferences but whenever I try to select anything other than 'Normal', I get "Desktop effects could not be enabled". I only have an 'on board' graphics card, so maybe it's that??

---

### Post by asmiller-ke6seh on 2007-11-23
First - regarding doing a new install of Gutsy - remember to back up your HOME directory so that you can restore all your data and essential configuration files after the installation is complete - then do a fresh GUTSY install.

What kind of graphics subsystem do you have? It is possible that it doesn't have the ability to support Compiz-Fusion.

Gutsy allows you to turn on a subset of the Compiz-Fusion functionality through the APPEARANCE controls - if your hardware will support it.

---

### Post by Cragrat on 2007-11-23
Not sure. All I know is that I don't have a separate Graphics Card and that the 'On Board' is (I think) 128mb.

---

### Post by bluepowder7 on 2007-11-23
what's the computer specs?  i'm also running on-board graphics on both the laptop (kinda inherent) and desktop, and fusion works well on both of them.  in one case, it's an intel graphics chipset, and in the other it's an nvidia, and each is stealing up to 256megs of my system ram.

---

### Post by Cragrat on 2007-11-23
What specs would you like to see? Sorry, still finding my way around the menus....

---

### Post by bluepowder7 on 2007-11-23
> **Cragrat said:**
> What specs would you like to see? Sorry, still finding my way around the menus....

what kinda computer do you have?  who makes it, what's the model number?

---

### Post by Cragrat on 2007-11-24
Compaq SR1619 - AMD Athlon 64 CPU - ATI Radeon Express Graphics - Bought from PC World 2 Years ago.

---

### Post by Ub1476 on 2007-11-24
Try this guide: [install 8.42.3 on RS482 [ ATI Radeon Xpress 200] on a fresh install Ubuntu 7.10 Gutsy ]("http://ubuntuforums.org/showthread.php?t=591066&highlight=ATI+Radeon+XPRESS+200")

It's for th latest driver from ATI, and those support the default AIGXL.

If you want to use the older drivers, you can check them in System>Administration>Restricted Driver Manager. Remember to install "xserver-xgl" if you decide to use those.

---

### Post by bluepowder7 on 2007-11-24
i did a quick search, and found a few guides.  try reading through them to see if they apply to you (might depend on which version of ubuntu you have, and the exact model of your card)

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

[http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)

[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)

---

### Post by Cragrat on 2007-11-25
I installed the ATI Accelerated Graphics Driver using the Restricted Drivers Manager.
The screen looks much better than before.
When I now go to 'Appearence preferences' -> 'Visual Effects' and try to select anything other than 'None', I no longer get "Desktop Effects Could Not Be Enabled" but "The Composite Extension Is Not Available" instead.
Sorry, you can tell that I'm avoiding using the Terminal like the plague. The main reason for this is that there's so many threads suggesting long & cumbersome solutions but nothing definitive.

---

### Post by Cragrat on 2007-11-25
Does this little lot help?
steve@study-pc:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
steve@study-pc:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
        Option          "UseFBDev"      "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
steve@study-pc:~$ lsmod
Module                  Size  Used by
af_packet              28172  2 
fglrx                 765588  11 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ipv6                  317192  12 
ppdev                  11272  0 
powernow_k8            16608  0 
cpufreq_ondemand       10896  1 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     9608  0 
cpufreq_powersave       3072  0 
cpufreq_userspace       6048  0 
container               6400  0 
dock                   12264  0 
ac                      7304  0 
sbs                    21520  0 
video                  21140  0 
button                 10400  0 
battery                12424  0 
sbp2                   27144  0 
lp                     15048  0 
snd_atiixp             24084  1 
snd_ac97_codec        122200  1 snd_atiixp
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             41896  1 
parport                44172  3 ppdev,lp,parport_pc
serio_raw               9092  0 
pcspkr                  4608  0 
psmouse                45596  0 
sg                     41384  0 
snd                    69288  12 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sd_mod                 32512  0 
k8temp                  7680  0 
soundcore              10272  1 snd
snd_page_alloc         12560  2 snd_atiixp,snd_pcm
i2c_piix4              11020  0 
i2c_core               30208  1 i2c_piix4
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
evdev                  13056  3 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
8139cp                 28032  0 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
ide_disk               20352  3 
usb_storage            81728  0 
libusual               22824  1 usb_storage
ata_generic             9988  0 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
8139too                31232  0 
mii                     7424  2 8139cp,8139too
ehci_hcd               40076  0 
atiixp                  7824  0 [permanent]
ide_core              141200  4 ide_cd,ide_disk,usb_storage,atiixp
ohci_hcd               25092  0 
usbcore               161584  5 usb_storage,libusual,ehci_hcd,ohci_hcd
sata_sil               14600  0 
libata                138928  2 ata_generic,sata_sil
scsi_mod              172856  5 sbp2,sg,sd_mod,usb_storage,libata
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor
steve@study-pc:~$

---

### Post by DutyDuty on 2007-11-25
When you want the box around it, use the button that looks like this : #
```
and you get this!
```

You have ATI graphics. Try finding the instructions for that.

---

### Post by Dark_X on 2007-11-25
I used XGL to get mine working.  It works great!

---

### Post by DutyDuty on 2007-11-25
You're going to have to use terminal at some point in Linux. It's a fact. You get comfortable with time. 

Yeah, I second XGL.

---

### Post by uBrendon on 2007-11-25
When I search compizconfig-settings-manager in synaptic nothing comes up help please. I'm in gusty and I'm on a Toshiba A135-S4656

---

### Post by DutyDuty on 2007-11-25
In synaptic, search "compizc"

That should return the package, if not, "compiz" will show it.

---

### Post by Cragrat on 2007-11-26
Thanks for your perseverance guys. I understand what you're saying but what's XGL exactly?

---

### Post by DutyDuty on 2007-11-26
XGL is (someone correct me if I'm wrong) an environment like GNOME, Blackbox, Fluxbox, etc. It's a sort of map that compiz runs well with.

---

### Post by Cragrat on 2007-11-27
OK. I seem to need XGL as well as Compiz-Fusion. I'm sorry. This is all getting way over my head. I don't understand what I need to get and how to install it. If I can't just download something and maybe enter just a few simple Terminal Commands, I think I'm going to have to give it all up.:(:(
I'm despondent now. I've come so far with this. This is the last hurdle to overcome before I stay with Ubuntu and not drift off back to Microsoft.

---

### Post by Cragrat on 2007-11-27
Yipee! I've got XGL!
Now have wobbly windows too. I've enabled the cube but it's still 2D.

---

### Post by amtur_poet on 2007-11-27
> **bluepowder7 said:**
> if you go to Synaptic, look for "compizconfig-settings-manager" and check it for installation.  it might have to download and install some other bits as well, so just OK those.

once it's installed, it'll show up under System - Preferences - Advanced Desktop Effects Settings
When I search for it in Synaptic, nothing comes up. I also tried to download the file manually, the package installer says "Error: Dependency is not satisfiable: python-compizconfig"
I also tried searching for "compiz" in synaptic, it said all the available packages were installed.

---


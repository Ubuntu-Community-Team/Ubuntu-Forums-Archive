---
title: "Onboard nic not detected - very frustrated"
date: 2005-12-12
forum: Desktop Environments
---

### Post by kook44 on 2005-12-12
Hi-
I know it is not proper etiquitte to cross-post, but I have been without a network connection for a few days, and I haven't gotten many replies to my other posts, so this is a last-dicth effort to see if anyone else has experienced anything similar.
It's very frustrating because ubuntu worked like a charm pn my old p3-733 clunker, and now I have this dual-core pc, and it's been kind of difficult getting everything working.

My previous post:
I have a dell deimension 9150 w/ onboard LAN.  In the windows device manager, the adapter is listed as Intel(R) PRO/1000 PL.
It is not detected by ubuntu.  I have done extensive searching online, and haven't found much.  The only thing I found was instructions to add the module to the kernel by typing "modprobe e1000".  I have done so, and there are no noticeable results.  When I type "ifconfig", only the loopback is listed.  If I try "ifup eth0" or "ifconfig eth0"  I recieve error messages saying the device does not exist.

This is the output of lspci:
```

0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corp.: Unknown device 27e0 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corp.: Unknown device 27e2 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b0 (rev 01)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 01)
0000:00:1f.2 0106: Intel Corp.: Unknown device 27c1 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70
0000:04:00.0 Ethernet controller: Intel Corp.: Unknown device 109a (rev 01)
0000:05:02.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0680 Ultra ATA-133 Host Controller (rev 02)
0000:05:04.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)


```
why are there so many "Unknown Diveces"  (including the Ethernet controller...)
and lsmod:
```

Module                  Size  Used by
e100                   32768  0
mii                     5248  1 e100
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
tsdev                   7616  0
rtc                    11832  0
pcspkr                  3652  0
ohci1394               30644  0
hw_random               5268  0
snd_hda_intel          15872  3
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  3
ide_disk               16128  3
usb_storage            64704  2
usbhid                 30688  0
siimage                11392  1
ahci                   11268  3
libata                 47876  1 ahci
scsi_mod              124872  6 sr_mod,sbp2,sd_mod,usb_storage,ahci,libata
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
piix                    9476  1
ide_core              125268  6 ide_disk,usb_storage,siimage,ide_cd,ide_generic,piix
unix                   24624  642
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon


```
I would appreciate any help - this is very frustrating!  :confused:

---

### Post by RAOF on 2005-12-12
If your motherboard is fairly new, it's possible that the Ubuntu kernels just don't include drivers for it.  You might want to check if a more recent kernel has support for your NIC.  If so, you'll need to build a new kernel from the lastest kernel sources.

---

### Post by kook44 on 2005-12-13
I'll give it a shot, but without a network connection, how will I get all the dependent packages?  How will I even know what they are?

---

### Post by RAOF on 2005-12-13
You'll need another computer with a working network.  Then, you can manually download the appropriate .deb files from a repository of your choice (like archive.ubuntu.com).  You will need to manually hunt down the dependencies though.  You can use apt-cache show <packagename> to view information about a package (like the dependencies).

Actually, now that I think about it, if you have an ubuntu computer with a working network, you could just build the kernel packages on there, and copy just the completed packages across.  In that case, I'd suggest following [this kernel howto]("https://wiki.ubuntu.com/KernelHowto"), replacing the following steps:
*) Rather than apt-getting the kernel source, download the latest source from kernel.org
*) Run "make oldconfig" rather than "make menuconfig" or "make xconfig" - this will select all the same options as the currently running kernel, and only ask about options that have changed between the kernel versions.  If in doubt about an option, make it a module if you can, or accept the default.  You can still run "make menuconfig" or xconfig afterward to fine-tune your config, if you desire.
*) Make sure that you build the packages with the --initrd option.

This should give you a bunch of kernel-foo-2.6.14 packages in the /usr/src directory.  You can now copy these to a CD, and install them on your networkless computer.

---

### Post by kook44 on 2005-12-13
Thanks guys.  I'm going to try it.  (first time compiling a kernel!)
I have a networked laptop running hoary (the desktop has breezy).  When trying to compile, will I have to upgrade the dependent packages to the version required by the new kernel, or do I just download their souce and somehow link them in the comilation process?  If the former, won't I run into problems b/c the updated packes are made to be used with the very kernel I'm trying to compile (which is newer that the one I'm running on the laptop)?

---

### Post by RAOF on 2005-12-13
The kernel doesn't actually depend on anything.  And you're not trying to install the kernel (on the laptop), just build it.  The hoary packages will do fine.

I'll add one final caution: manually compiling the kernel won't build the restricted-packages for it, so if you have any hardware that is supported by non-free drivers (like an nvidia or ati graphics card), you'll also need to manually rebuild those drivers if you want them.

---

### Post by kook44 on 2005-12-14
Ok-
I compiled the kermel succesfully, and copied to the machine.  when I ran 
dpkg -i <kernel>
I got an error about missing initrc-tools.  So, I downloaded the pkg from packages.ubuntu.com and tried to install it- I got another dependency error for the initrc-tools package.  Is there a certain group of packages that need to be installed in order to install a new kernel?

---

### Post by RAOF on 2005-12-14
Checking out the apt-cache show initrd-tools, it looks like you'll also need the packages:
coreutils or fileutils (>= 4.1.9) or stat (>= 3.0), 
cpio 
cramfsprogs (>= 1.1-4)
dash
util-linux (>= 2.11b-3)
lsb-base (>= 1.3-9ubuntu3)

I can't suggest anything more than progressively downloading dependencies until they're all fixed, sorry.

---


---
title: "New Kernal.  No Sound."
date: 2009-05-22
forum: General Help
---

### Post by Zeenomorph on 2009-05-22
The kernal was updated not so long ago.  Since then I have no sound.  Just a little "x" over my speaker icon.  I click on it, and it tells me that I don't have GStreamer plugins.  I went to add/remove saw that I had them.  Unintsalled them, and re-installed them.  Still no sound.

Now I have to select the previous kernel from the Grub menu.  When I do this my sound works like it always did.

I thought I would wait a bit before posting hoping that it would be patched / hotfixed, but it's still not working.  I would like to get this fixed.

Any advice would be appreciated.

---

### Post by Bender2k14 on 2009-05-22
Do you have a sound card?....What sound card?

Do you have integrated sound?....What is your motherboard?

---

### Post by Zeenomorph on 2009-05-22
Those seem like very good questions.  

How would I go about answering them?

---

### Post by Bender2k14 on 2009-05-22
I am guessing that you did not build this computer yourself, so what is the manufacture and model number for your computer?

---

### Post by Zeenomorph on 2009-05-22
I got it from System 76.  They ship computers with Ubuntu preinstalled.

It's worked for years, and still the previous kernel works.  It's just this new one.  I guess I'm to assume that I'm alone in my troubles?

Where would I check to see my sound card?  It's a good computer, I purchased it for gaming, so I assume that it's not integrated sound.  But, alas, I'm just not sure.

---

### Post by Soul-Sing on 2009-05-23
After a kernel update on hardy i have got exact the same problem.
Not all the [COLOR="DarkOrange"]kernel[/COLOR] packages were installed, an kernel update comes with a package: the image/headers/modules/etc. 1 package wasn't installed. Installing this [COLOR="DarkOrange"]missing "kenel"[/COLOR] package solved my gstreamer/sound problem.

---

### Post by Zeenomorph on 2009-05-23
...and how would I go about installing this missing package?

---

### Post by Soul-Sing on 2009-05-23
> **Zeenomorph said:**
> ...and how would I go about installing this missing package?

Synaptic gives you a glimp of the recent kernel update: historie option maybe?
Which kernelpackages were installed?

---

### Post by Zeenomorph on 2009-05-23
I typed kernel package into Synaptic, and these are highlighted;

acpid 
alsa-base
alsa-oss
apport
apport-gtk
binutils-static
debianutils
fuse-utils
gnome-pilot
ia32-libs
initramfs-tools
iproute
iproute-dev
iptables
jockey-common
jockey-gtk
laptop-mode-tools
libapm1
libdevmapper1.02.1
libdrm2
libfuse2
libkeyutils1
libntfs-3g23
libselinux1
libsysfs2
linux-headers-2.6.24-16
linux-headers-2.6.24-16-generic
linux-headers-2.6.24-17
linux-headers-2.6.24-17-generic
linux-headers-2.6.24-18
linux-headers-2.6.24-18-generic
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
**(also the same thing through to -24**
linux-headers-generic
linux-image-2.6.24-23-generic
linux-image-2.6.24-24-generic
linux-libc-dev
linux-restricted-modules-generic
linux-unbuntu-modules-2.6.24-23-generic
module-init-tools
net-tools
nvidia-kernel-common
pcmciautils
procps
util-linux
xserver-xorg-input-evdev
xserver-xorg-input-wacom

...phew, I sure hope that was helpful!

---

### Post by hal8000 on 2009-05-23
You need to collec some information. lets start with the sound card.Post the output of this command please:

sudo lspci


The above lists all hardware connected to the PCI bus. If theres a soundcard or built in sound hardware it will be detected.

Once your sound card is known, its a matter of seeing if the respective kernel modules have been loaded and possibly making an entry in/etc/modules (only if needed).

---

### Post by Zeenomorph on 2009-05-23
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by Zeenomorph on 2009-05-24
Don't mean to bump my own post, but is there anything I can do?

I thought it would be simple seeing as my sound works in the old kernel, as well as in windows.  It's just this new kernel where my sound doesn't work.

---

### Post by hal8000 on 2009-05-24
> **Zeenomorph said:**
> 00:00.0 Host bridge: Intel Corporation
 --snip
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
--snip
IEEE-1394a-2000 Controller (PHY/Link)

OK,now we're getting somewhere. Your soundcard is built-in and uses Intel ICH9 chipset.

Now lets see what your kernel has loaded. Please post output of:

uname -a

and also

lsmod | grep snd


Chances are theres a missing module or incorrect module loaded.

---

### Post by Zeenomorph on 2009-05-25
uname -a output;

Linux Mojo 2.6.24-24-generic #1 SMP Wed Apr 15 15:11:35 UTC 2009 x86_64 GNU/Linux

lsmod output;

Module                  Size  Used by
ipv6                  311848  523 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67620  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  0 
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       11152  4 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       6180  0 
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
dock                   12960  0 
sbshc                   8960  1 sbs
container               6656  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
uinput                 11904  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
nvidia               8858052  34 
usbhid                 35680  0 
hid                    44992  1 usbhid
i2c_core               28544  1 nvidia
iTCO_wdt               15312  0 
psmouse                46236  0 
evdev                  14976  7 
button                 10912  0 
intel_agp              30624  0 
serio_raw               9092  0 
iTCO_vendor_support     5764  1 iTCO_wdt
e1000e                108196  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sd_mod                 33280  3 
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
ata_piix               24196  2 
ata_generic             9988  0 
pata_marvell            9472  0 
pata_acpi               9856  0 
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
libata                176560  4 ata_piix,ata_generic,pata_marvell,pata_acpi
scsi_mod              178488  5 sbp2,sd_mod,sg,sr_mod,libata
ehci_hcd               41996  0 
uhci_hcd               29856  0 
usbcore               170288  4 usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              40424  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

grep snd output;

nothing.  Terminal remained blank.

---

### Post by Soul-Sing on 2009-05-25
I collected all commands here from my ./bash direct.( that toke some time...:) )

On my computer (hardy) -24 kernel

```
sudo apt-get install linux-ubuntu-modules-2.6.24-24 generic
```

did the trick, after a reboot, my sound and gstreamer problem was solved. (somehow this module wasn't installed correctly on my computer.

---

### Post by Zeenomorph on 2009-05-25
E: Couldn't find package linux-unbuntu-modules-2.6.24-24

---

### Post by Soul-Sing on 2009-05-25
Give it a try, i made a mistake, and corrected it now....
(sorry bout that)

```
sudo apt-get install linux-ubuntu-modules-2.6.24-24 generic
```

reboot

---

### Post by hal8000 on 2009-05-25
> **Zeenomorph said:**
> uname -a output;

Linux Mojo 2.6.24-24-generic #1 SMP Wed Apr 15 15:11:35 UTC 2009 x86_64 GNU/Linux


grep snd output;

nothing.  Terminal remained blank.

From the terminal try

sudo depmod -aev
sudo modpobe snd-intel8x0
sudo modprobe soundcore

Now adjust volume control and try and play a sound file or audio CD.
Is your sound working?

The sound modules should be located in

/lib/modules/ker-version/kernel/sound

If sound works you now make this permanent.

On Gutsy there was update-modules as sudo, however that command
has been deprecated. If you are using gutsy or earlier it may work
failing that entering each module on a line in
/etc/modules

should load the sound modules next reboot
Hal



Just replace ker-version with your kernel version.

---

### Post by Zeenomorph on 2009-05-25
To leoquant;
E: Couldn't find package linux-ubuntu-modules-2.6.24-24

To hal8000;
sudo: modpobe: command not found



I still seem to be stuck here...

---

### Post by Zeenomorph on 2009-05-26
I hope that i'm not breaching the rules of etiquette here by bumping my own thread again, but I'm still hoping for a solution.

Do I need to reinstall Ubuntu?  Am I screwed here?

---

### Post by hal8000 on 2009-05-27
> **Zeenomorph said:**
> To leoquant;
E: Couldn't find package linux-ubuntu-modules-2.6.24-24

To hal8000;
sudo: modpobe: command not found



I still seem to be stuck here...


Just came to review my own posts.

Its modprobe   (in your typo you omitted "r")

You may also have to type

sudo apt-get install linux-ubuntu-modules-2.6.24-24

as this appears to be missing in your system.

---

### Post by Zeenomorph on 2009-05-27
mojo@Mojo:~$ sudo modprobe snd-intel8x0

FATAL: Module snd_intel8x0 not found.


mojo@Mojo:~$ sudo apt-get install linux-ubuntu-modules-2.6.24-24

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package linux-ubuntu-modules-2.6.24-24



I don't seem to be getting anywhere.  This is frustrating.

---

### Post by Soul-Sing on 2009-05-27
```
sudo apt-get install linux-ubuntu-modules-'uname -r'
```
reboot should clear your issues.
```

sudo apt-get install linux-ubuntu-modules-`uname -r`
```
or with this syntax...

---

### Post by Zeenomorph on 2009-05-30
I'VE GOT SOUND!

Thank you so much Leoquant!  It was the 2nd code box that worked.  

I really appreciate your help in this.  Thank you again!

---

### Post by Soul-Sing on 2009-05-30
> **Zeenomorph said:**
> I'VE GOT SOUND!

Thank you so much Leoquant!  It was the 2nd code box that worked.  

I really appreciate your help in this.  Thank you again!

Great! :D

---

### Post by ububaba on 2009-05-30
> **leoquant said:**
> ```
sudo apt-get install linux-ubuntu-modules-'uname -r'
```
reboot should clear your issues.
```

sudo apt-get install linux-ubuntu-modules-`uname -r`
```
or with this syntax...

Used the above. The results points out for [COLOR="Red"]not having[/COLOR] linux-ubuntu-modules-2.6.27-14-generic
```
sudo apt-get install linux-ubuntu-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.27-14-generic

```
Next step? Thanks.

---

### Post by Zeenomorph on 2009-10-23
I'm Baaaaack.....

The new kernel caused the same issue again.

I remembered the problem, and checked on my old post here, and the solution worked.

I'm just wondering if this will happen every time there is a new kernel?  What's going on that when a new kernel comes out I lose my sound?

Zeeno

---


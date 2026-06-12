---
title: "Successful D620 Fiesty 64bit install : ipw3945 gm965 video"
date: 2007-08-06
forum: Dell  Ubuntu Support
---

### Post by cacycleworks on 2007-08-06
I've been banging my head against the wall for over a week getting 64 bit install to run with 1440x900 intel gm965 video, sound, and Intel Corporation PRO/Wireless 3945ABG wireless. 

[SIZE="2"](nvidia video and dell wireless use ndis wrapper) 4965 wireless? got me. the Intel site totally melted my brain.
[/SIZE]


I finally fingered it out. I had given up in a fit and reinstalled the OS yet again. But this time it worked. all the knowledge I had accumulated in my 30 odd hours of troubleshooting got me the perfect solution.

Here's the recipe I used (nearly all actions require root privilege):

**To be root**
The way I do all the sudo things easily:
$ sudo su
(enter password)
# apt-get or nano blah blah blah


**CD**
7.04 kubuntu alt amd64 cd  from here:
kubuntu-7.04-alternate-amd64.iso [http://mirrors.cs.wmich.edu/ubuntu-releases/kubuntu/feisty/kubuntu-7.04-alternate-amd64.iso](http://mirrors.cs.wmich.edu/ubuntu-releases/kubuntu/feisty/kubuntu-7.04-alternate-amd64.iso)

I ensure my /home is on its own partition. Makes installing a new distribution trivial. And most/all of your tweaks survive!

My partition map:
primary partition: /dev/sda1 on /boot type ext3 (bootable) 200M
primary partition: /dev/sda2 on / type ext3  15GB for root
primary partition: /dev/sda3 on /usr type ext3 14.8 GB for /usr
Extended partition: /dev/sda4 (which doesn't show up)
Logical Drive in extended partition: /dev/sda5 on /tmp type ext3  8GB
Logical Drive in extended partition: /dev/sda6 on /home type ext3  80GB  (never ever format this!)
Logical Drive in extended partition: /dev/sda7 is swap 2GB

I reformat all but the /home on /dev/sda6. :) 


**Update Grub**
upon initial boot, I hit esc to enter grub. Then I pressed e to edit top entry then e again on the line with all the options. At the end of the line I removed the quiet splash and added pci=assign-busses

I want to have all the text fly by upon start up, so I kill the quiet and splash.

To make the Grub edit "stick", you will need to do these steps:
If you edit your menu.lst manually, you want to make sure to edit the "# kopt=" line (leave it commented), or the "# defoptions" line, then run "sudo update-grub".
If you manually edit the options on the boot line of your various kernels, they'll be wiped out each time menu.lst gets updated (by having a new kernel installed, for example).

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=[COLOR="Red"]vga=792 pci=assign-busses[/COLOR]

I added the RED text to the file and then ran sudo update-grub and reloaded the menu.list file and the change now shows up on all entries!
(you will be able to log into a GUI environment here!)

**update distribution**
edit the /etc/apt/sources.list file and remove the line with the CD-Rom in it that doesn't have the # at its beginning.

apt-get update
apt-get upgrade
apt-get dist-upgrade

This gets you linux kernel 2.6.20-16-generic

before restarting, check your grub menu.list that pci=assign-busses is still there!! If not, repeat above steps.


**edit modules**
For editing, I use sudo su and then vi in a terminal / konsole window. Or you can use Alt-F2 kdesu kwrite to accomplish the same.

I was a total punk -- and some of this may not be needed -- but I added the three lines:
piix
snd_hda_intel
agpgart

to BOTH files: **/etc/modules** and **/etc/initramfs-tools/modules**

After the edit, you must run [FONT="Courier New"]**update-initramfs -u**[/FONT]  !!


**my "oopsie"**
when I went through the process of getting the back ported 64bit xserver-xorg files, i did a dumba$$ move and ran a apt-get remove xserver-core.  Please don't do that... to recover, I had to work all kinds of stupidity of installing kubuntu-desktop and then I had to use "aptitude" to suggest to me things to do to resolve my problems.

**fix the video**
download and install the two files from here: 
[http://ubuntuforums.org/showthread.php?t=500668](http://ubuntuforums.org/showthread.php?t=500668)

dpkg-reconfigure xserver-xorg

options I used:
no autodetect  -enter-
I called the vid card GM965 -enter-
-enter-
It defaulted to my pci address PCI:0:2:0  -enter-
i entered in 256 for the memory    -enter-
use kernel framebuffer? -no-    -enter-
autodetect kybd? -no-    -enter-
kybd layout: us   -enter-
xbd set to use: xorg    -enter-
pc104    -enter-
(use defaults)
then no 3 button emulation
(default on the xserver modules)
yes to write files to default config location      -enter-
-no- to autodetect monitor     -enter-
I named the monitor dell 1440x900 laptop     -enter-
I selected:
[*] 1440x900 
[*] 1280x800   (i don't know if this is valid, who cares, really)
[*] 1024x768
[*] 800x600
and cleared all other resolutions.   -enter-
-medium-           -enter-
1440x900@100hz      -enter-
Write monitor sync changes to config file?  -yes-     -enter-
24 color depth     -enter-

Then I go into the /etc/X11/xorg.conf file and get rid of the wacom crap as well as the "devices" created by them: stylus, eraser, and cursor (which are listed in the section "ServerLayout" near the bottom)

Seriously, that was it. I think...   ;)

lspci:
root@outside:/etc/X11# lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
04:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
04:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
root@outside:/etc/X11#

I'm so glad I found a solution. I've spent way too much time on this instead of loving family or working at work!

---

### Post by cacycleworks on 2007-08-06
BTW:

The "pci=assign-busses" is what I believe enables wireless (and maybe sound) to happen...

see...
root@outside:/etc/network# lshw
outside
    description: Portable Computer
    product: Latitude D630
    vendor: Dell Inc.
    serial: 7K962D1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-4B00-1039-8036-B7C04F324431

        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0c:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:fe8ff000-fe8fffff irq:17

---------------------------------------------------------------------------------
lspci relevant output:
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)


The wireless is buried under the PCI bridge 1c.0 ...

and without the pci=assign-busses, dmesg would have this:

[   11.144313] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.144329] PCI: Probing PCI hardware (bus 00)
[   11.144343] PM: Adding info for No Bus:pci0000:00
[   11.146052] PCI: Transparent bridge - 0000:00:1e.0
[   11.146130] PCI: Bus #04 (-#07) is hidden behind transparent bridge #03 (-#04) (try 'pci=assign-busses')
[   11.146134] Please report the result to linux-kernel to fix this permanently

While that's not the 1c.0 bride, the same applied to all the PCI bridges... once this issue was fixed, suddenly the ipw3945 started showing up.



piix gets you DMA and your CD/DVD drive
hda_snd_intel   is what tells the kernel to use for sound
agpgart is for xvideo to run with the intel driver.


Now, it's my humble observation that it is possible the ICH8 82801 family of chipsets is putting most of the confusion on this board. In my research, I'm finding this affects MANY makes... HP, Dell, ... everyone who uses a mostly-Intel install that is pretty new.

chris@outside:~/d630$ dmesg | grep ICH
[   11.556807] ICH8M: IDE controller at PCI slot 0000:00:1f.1
[   11.557025] ICH8M: chipset revision 2
[   11.557082] ICH8M: not 100% native mode: will probe irqs later
chris@outside:~/d630$

---


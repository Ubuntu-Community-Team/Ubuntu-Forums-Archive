---
title: "Wireless card not detected on Mini 10v"
date: 2012-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chinchillas on 2012-07-28
Hi, my wireless card is not detected or simply not working. 
This in my info:

chinchilla-u@chinchilla-ubuntu:~$ sudo lshw -c network
[sudo] password for chinchilla-u: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:9d:59:74
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=x.x.x.x latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff

This is after entering the commands I found on thread [http://ubuntuforums.org/showthread.php?t=1928241:](http://ubuntuforums.org/showthread.php?t=1928241:)

sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

Any ideas? I can only connect via Ethernet.

I'm using Dell Inspiron Mini 10v, 160 GB,  Ubuntu 12.4.

---

### Post by wildmanne39 on 2012-07-29
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by chinchillas on 2012-07-29
```

chinchilla-u@chinchilla-ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux chinchilla-ubuntu 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux
chinchilla-u@chinchilla-ubuntu:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:02f4]
    Kernel driver in use: r8169
chinchilla-u@chinchilla-ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 174f:1403 Syntek Integrated Webcam
chinchilla-u@chinchilla-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chinchilla-u@chinchilla-ubuntu:~$ rfkill list all
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
chinchilla-u@chinchilla-ubuntu:~$ lsmod


```

---

### Post by wildmanne39 on 2012-07-29
Hi, I do not see your wireless card so it is either turned off in the bios or is defective, go into your bios and see if you have an option to turn wireless lan on.

Also please post the output of:
```
lsmod
lspci -nn
sudo pccardctl ident
```
Thanks

---

### Post by chinchillas on 2012-07-31
Hi, these are the results: 
```

chinchilla-u@chinchilla-ubuntu:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_realtek   174134  1 
dell_laptop            17767  0 
compal_laptop          19315  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ums_realtek            17920  0 
uas                    17828  0 
uvcvideo               67203  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               86588  1 uvcvideo
psmouse                72919  0 
i915                  414703  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158438  8 bnep,rfcomm
drm                   197692  4 i915,drm_kms_helper
ppdev                  12849  0 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  1 ums_realtek
r8169                  56321  0 
chinchilla-u@chinchilla-ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
chinchilla-u@chinchilla-ubuntu:~$ sudo pccardctl ident



```Do you think my card got damaged? Should I remove-reinstall it? I'm having the same problem with my video card; it doesn't recognize a VGA cable when I plug it.
Thank you for your help.

---

### Post by wildmanne39 on 2012-07-31
Hi, if this is a desktop then open the case and remove the card and reset it or try another pci slot.
Thanks

---

### Post by chinchillas on 2012-07-31
No, it's a netbook :(

---

### Post by wildmanne39 on 2012-07-31
Hi, I have the same issue on my old laptop my wireless card just went out a few days ago so I am going to but an usb adapter.

There is nothing else that I know to do.
Thanks

---

### Post by chinchillas on 2012-07-31
> **wildmanne39 said:**
> Hi, I have the same issue on my old laptop my wireless card just went out a few days ago so I am going to but an usb adapter.

There is nothing else that I know to do.
Thanks

Thank you. I think I'm gonna send it to the tech or just let it rest :(

---

### Post by ugm6hr on 2012-08-03
Does seem like there is a hardware issue here.
Worth unscrewing the back cover, and making sure the wifi card is plugged in securely.

---

### Post by chinchillas on 2012-08-05
I unplugged and re plugged the antennas of the  Broadcom wireless card and the computer still won't recognize it. Do you think my card simply stopped working? Is there another way to "pin" it? I should mention that I installed Ubuntu because my main system, Windows XP SP3, got accidentally wiped out and I couldn't reinstall it from an USB card after many attempts. Do you think among the "wipe-out" I erased a driver? Shouldn't this be noticeable by the Ubuntu install?
Thanks for your replies.

---

### Post by ugm6hr on 2012-08-05
> **chinchillas said:**
> Do you think my card simply stopped working? Is there another way to "pin" it?
Yes - just stopped working. Electronics do that sometimes. If it isn't because of a loose connection, then it's probably a true hardware fault.
> **chinchillas said:**
> I should mention that I installed Ubuntu because my main system, Windows XP SP3, got accidentally wiped out and I couldn't reinstall it from an USB card after many attempts. Do you think among the "wipe-out" I erased a driver? Shouldn't this be noticeable by the Ubuntu install?
Thanks for your replies.
Did the card immediately stop working when you installed Ubuntu - i.e. working fine on XP one minute, then not working on Ubuntu on fresh install? Did it ever work on Ubuntu? Not sure whether the answer will change my view, but it does make it seem an unfortunate coincidence.
This has nothing to do with drivers or software. I can say this with authority, since "sudo lshw -c network" and "lspci" do not show any evidence of a wifi card at all - i.e no hardware is detected. It may be worth checking if there is any sign of a card on "lsusb" - because some internal wifi cards are recognised as usb rather than internal, although I do not believe this is true of any of the Dell Mini range.

Honestly, I think this is likely a terminal hardware fault - and I'm not sure whether the Mini's wifi card can be easily replaced (since I have never tried removing mine).

---

### Post by wildmanne39 on 2012-08-05
Hi, you have already posted lsusb and it showed nothing, sometimes people have reported that  unplugging the computer and removing the battery for about 30 minutes then putting the battery back in and booting up fixes the recognition issue, but I am almost positive it has failed, and as stated even with no driver installed the device should show up.
Thanks

---


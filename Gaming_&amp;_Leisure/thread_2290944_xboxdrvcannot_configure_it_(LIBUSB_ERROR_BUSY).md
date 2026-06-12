---
title: "xboxdrv:cannot configure it (LIBUSB_ERROR_BUSY)"
date: 2015-08-16
forum: Gaming &amp; Leisure
---

### Post by YpeKPbW on 2015-08-16
Hi all!

I'm struggling with xboxdrv to get less sensitivity on my Xbox 360 wireless controller and to be able to use it in my emulators of "retrogaming" machines...

The error I encounter is this:
```
$ sudo xboxdrv --deadzone 8000
xboxdrv 0.8.5 - http://pingus.seul.org/~grumbel/xboxdrv/ 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Wireless Controller (PC)
Vendor/Product:    045e:0719
USB Path:          003:006
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

-- [ ERROR ] ------------------------------------------------------
 Error couldn't claim the USB interface: LIBUSB_ERROR_BUSY
```

I've installed xboxdrv on my Xubuntu 14.04.3 using [this version]("https://github.com/raelgc/ubuntu_xboxdrv"); xpad it's already removed.

I don't understand what is "using/holding" the USB interface...


Could someone guide me to the resolution?

Thank you

---

### Post by ODTech on 2015-08-17
In my case earlier today jstest.gtk was holding the usb interface. Removing it fixed the issue.

FYI the steamos xpad driver works realy well too if you want to give it a go.

---

### Post by YpeKPbW on 2015-08-17
> **ODTech said:**
> In my case earlier today jstest.gtk was holding the usb interface. Removing it fixed the issue.

FYI the steamos xpad driver works realy well too if you want to give it a go.

If I try to apt-get remove the jstest.gtk package it will also remove the xboxdrv-ubuntu package I use... :(

---

### Post by M3m3nt0 on 2015-08-18
Just to test, I've installed ubuntu-xboxdrv package on another Ubuntu 14.04 machine with the same results :(

There are others tests I could make or configuration I could change???

---

### Post by ODTech on 2015-08-18
> **M3m3nt0 said:**
> Just to test, I've installed ubuntu-xboxdrv package on another Ubuntu 14.04 machine with the same results :(

There are others tests I could make or configuration I could change???

To see what drivers are loaded do the following

```
sudo lsmod
```

See if you can spot anything controller related like xpad or xboxdrv.

For me jstest.gtk did not show as a driver but i suspect it runs as a service instead. Use the gnome process monitor to check for it.
I took it off my machine when i installed the steamos driver so i can't check mine to compare.

---

### Post by M3m3nt0 on 2015-08-19
> **ODTech said:**
> To see what drivers are loaded do the following

```
sudo lsmod
```

See if you can spot anything controller related like xpad or xboxdrv.

For me jstest.gtk did not show as a driver but i suspect it runs as a service instead. Use the gnome process monitor to check for it.
I took it off my machine when i installed the steamos driver so i can't check mine to compare.

This is the output of lsmod (this is the laptop with Ubuntu 14.04):
```
Module                  Size  Used by
ctr                    13049  3 
ccm                    17773  3 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65626  1 
rfcomm                 69160  8 
btusb                  32412  0 
bnep                   19624  2 
bluetooth             391136  22 bnep,btusb,rfcomm
snd_hda_intel          56531  3 
snd_hda_codec         192980  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
coretemp               13435  0 
kvm_intel             143187  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
arc4                   12608  2 
videobuf2_core         40664  1 uvcvideo
kvm                   455794  1 kvm_intel
videodev              134688  2 uvcvideo,videobuf2_core
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13462  0 
snd_timer              29482  2 snd_pcm,snd_seq
toshiba_acpi           22901  0 
rtl8192se              63196  0 
sparse_keymap          13948  1 toshiba_acpi
lpc_ich                21080  0 
wmi                    19177  1 toshiba_acpi
snd                    69322  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
toshiba_bluetooth      12852  0 
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
mac80211              630728  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi
shpchp                 37032  0 
mac_hid                13205  0 
i915                  784116  3 
soundcore              12680  1 snd
video                  19476  1 i915
drm_kms_helper         55071  1 i915
drm                   303102  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106647  0 
ahci                   34091  2 
libahci                32716  1 ahci
r8169                  67581  0 
sdhci_pci              23172  0 
sdhci                  43015  1 sdhci_pci
mii                    13934  1 r8169
```

I've also checked the process monitor but I cannot see anything that ring the bell...but maybe I don't know what to look for...
How could I "print/output" the list of services/processes to paste it here?

---

### Post by M3m3nt0 on 2015-08-19
FYI
I just tried on a new (live) Ubuntu 14.04 system just installing the ubuntu-xboxdrv package and I get the same error :(

I noticed that if I start it with --detach-kernel-driver argument it gives me another error:
```
$ sudo xboxdrv --detach-kernel-driver
xboxdrv 0.8.5 - http://pingus.seul.org/~grumbel/xboxdrv/ 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Wireless Controller (PC)
Vendor/Product:    045e:0719
USB Path:          006:002
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

-- [ ERROR ] ------------------------------------------------------
 Error couldn't claim the USB interface: LIBUSB_ERROR_NOT_FOUND
Try to run 'rmmod xpad' and then xboxdrv again or start xboxdrv with the option --detach-kernel-driver.

ubuntu@ubuntu:~$ sudo xboxdrv
xboxdrv 0.8.5 - http://pingus.seul.org/~grumbel/xboxdrv/ 
Copyright © 2008-2011 Ingo Ruhnke <grumbel@gmx.de> 
Licensed under GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html> 
This program comes with ABSOLUTELY NO WARRANTY. 
This is free software, and you are welcome to redistribute it under certain 
conditions; see the file COPYING for details. 

Controller:        Microsoft Xbox 360 Wireless Controller (PC)
Vendor/Product:    045e:0719
USB Path:          006:002
Wireless Port:     0
Controller Type:   Xbox360 (wireless)

-- [ ERROR ] ------------------------------------------------------
 Error couldn't claim the USB interface: LIBUSB_ERROR_BUSY
Try to run 'rmmod xpad' and then xboxdrv again or start xboxdrv with the option --detach-kernel-driver.

```

---

### Post by M3m3nt0 on 2015-08-19
OK I think I found "the problem"! :)

If I stop the xboxdrv service, then I could start it for the terminal (using all the switches I need).

I tried to start it from the terminal because I would try some switches (like the one for the sensibility) to tune my controller; I would eventually start another topic on this! :D

Thank you **ODTech**!

---

### Post by seansplayin on 2015-08-29
I struggled trying to get my xbox360 wireless controllers working for many many hours in both Ubuntu 12.04/12.04 and Linux Mint 17.2. I would get xboxdrv:cannot configure it (LIBUSB_ERROR_BUSY) if ran under sudo and access denied if ran under regular user. what I found is that the OS had a xpad driver (windows term) installed that was not letting xboxdrv and ubuntu-xboxdrv take control of the USB device. After following more than a dozen tutorials I found one article that literally explains everything about the controllers [https://wiki.archlinux.org/index.php/Gamepad](https://wiki.archlinux.org/index.php/Gamepad) 
My take away was that if I installed the steamos-xpad-dkms it would update the integraded xpad driver (package) and fix the controllers incorrectly mapped key's, solve the blinking 4 LED's, load on boot and simply work. I followed these instructions     [http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working](http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working)        to install Steamos-xpad-dkms and the controller works now. you may still have to adjust the dead bank for your analog sticks but other than that is works great.... good luck. 

sudo add-apt-repository ppa:mdeslaur/steamos
sudo apt-get update
sudo apt-get install steamos-xpad-dkms

---


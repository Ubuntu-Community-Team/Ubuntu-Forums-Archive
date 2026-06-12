---
title: "Animations stutter when exiting the Activities"
date: 2016-08-29
forum: Desktop Environments
---

### Post by tomkis90 on 2016-08-29
I have upgraded everything and my computer is too powerful to have such issues imo.
i7 4790k,8gb ram, gtx 980.

Entering the activities is always nice and smooth but exiting always causes stuttering, sometimes less, sometimes more.

Edit: I use the newest version of Ubuntu which is 16.04.1

---

### Post by #&amp;thj^% on 2016-08-29
What is the output of this from the terminal
```
 inxi -FG 
```
Paste it back here using code tags..to help read the output.

---

### Post by tomkis90 on 2016-08-29
```
[SIZE=2]System:    Host: tomas-MS-7918 Kernel: 4.4.0-34-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.5 Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MSI model: Z97 GAMING 3 (MS-7918) v: 1.0
           Bios: American Megatrends v: V2.0 date: 04/22/2014
CPU:       Quad core Intel Core i7-4790K (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 4400 MHz 1: 4397 MHz 2: 4396 MHz 3: 4172 MHz
           4: 4365 MHz 5: 4181 MHz 6: 4379 MHz 7: 4371 MHz 8: 4201 MHz
Graphics:  Card: NVIDIA GM204 [GeForce GTX 980]
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 980/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 361.42
Audio:     Card-1 NVIDIA GM204 High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Intel 9 Series Family HD Audio Controller
           driver: snd_hda_intel
           Card-3 Samson C03U multi-pattern microphone driver: USB Audio
           Card-4 Logitech HD Webcam C525 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.4.0-34-generic
Network:   Card: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller
           driver: alx
           IF: enp3s0 state: up speed: 100 Mbps duplex: full
           mac: 44:8a:5b:a0:9e:aa
Drives:    HDD Total Size: 1120.2GB (4.4% used)
           ID-1: /dev/sda model: WDC_WD10EZEX size: 1000.2GB
           ID-2: /dev/sdb model: KINGSTON_SV300S3 size: 120.0GB
Partition: ID-1: / size: 102G used: 9.8G (11%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 473M used: 112M (25%) fs: ext2 dev: /dev/sdb2
           ID-3: swap-1 size: 0.51GB used: 0.00GB (0%) fs: swap dev: /dev/sda1
           ID-4: swap-2 size: 8.54GB used: 0.00GB (0%) fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 53C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 290 Uptime: 8 min Memory: 2302.7/7929.7MB
           Client: Shell (bash) inxi: 2.2.35[/SIZE]
```

---

### Post by #&amp;thj^% on 2016-08-29
You are right..there should be no issues with your setup
```

[SIZE=2]Graphics:  Card: NVIDIA GM204 [GeForce GTX 980]
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 980/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 361.42

```
You do have the proper driver installed...All though I do not use Gnome.
And I don't think GNOME allows you to change the compositor or window manager. 
Sorry I was not more helpful here.

[/SIZE]

---

### Post by tomkis90 on 2016-08-29
I am thinking it could be caused by certain software that I use, that needs gpu acceleration, that would be my only lead, but even then, its a gtx 980, its an overkill in every single way.

---

### Post by #&amp;thj^% on 2016-08-29
I totally agree that certain apps demand a compositor to enhance the performance..but that said Gnome uses its own window manager and dose not play nicely with those kind of Applications.
My self I use [Mate DE]("http://mate-desktop.org/") with Compiz and I have no reason to look further...everything thing just works a treat. But that is just my preference.

---

### Post by tomkis90 on 2016-08-29
I have made a new discovery, if i watch youtube in full screen everything works very smoothly, as soon as i "un-fullscreen" a video its gets pretty choppy again. this is interesting.

---


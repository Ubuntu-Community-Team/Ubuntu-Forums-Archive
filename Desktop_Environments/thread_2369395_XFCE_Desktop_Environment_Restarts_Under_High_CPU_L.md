---
title: "XFCE Desktop Environment Restarts Under High CPU Load"
date: 2017-08-22
forum: Desktop Environments
---

### Post by scrawn331 on 2017-08-22
Hi, I'm coming from regular Ubuntu to Xubuntu because Unity does not play nicely with my Lenovo P50 laptop. In fact, the only DE that seems to run okay on this laptop is XFCE. However, when I switched over to Xubuntu, I find that under high CPU load, the DE restarts. I get kicked back out to the login prompt and all of my running applications have been closed. I did not see this problem when I was running XFCE as the DE in Ubuntu. It happens both when I have external monitors connected and running just on the laptop display. I'm not sure where to start looking for where this problem occurs, any advice?

---

### Post by Autodave on 2017-08-22
How much RAM is in there? You may want to run a memory test to see if you have a RAM chip(s) going bad.

---

### Post by ajgreeny on 2017-08-22
What hardware does that laptop have?  I am aware that it is quite a powerful machine, and the only reference I have found suggests it has an nvidia graphic card; if so what driver do you have for it?

Show us the output of command ```
inxi -F
``` in terminal.  You may need to install **inxi** first as I am not sure if it is a default install.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by scrawn331 on 2017-08-22
> **Autodave said:**
> How much RAM is in there? You may want to run a memory test to see if you have a RAM chip(s) going bad.

16GB. I just got finished running a shorter memtest (skipping some of the longer tests like bit fade and hammer) and it did not find any errors. I will run a full test tonight and report back.

---

### Post by scrawn331 on 2017-08-22
> **ajgreeny said:**
> What hardware does that laptop have?  I am aware that it is quite a powerful machine, and the only reference I have found suggests it has an nvidia graphic card; if so what driver do you have for it?

Show us the output of command ```
inxi -F
``` in terminal.  You may need to install **inxi** first as I am not sure if it is a default install.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

```

System:    Host: scrawn331 Kernel: 4.10.0-32-generic x86_64 (64 bit) Desktop: Xfce 4.12.3
           Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 20ENCTO1WW v: ThinkPad P50
           Mobo: LENOVO model: 20ENCTO1WW v: SDK0J40697 WIN Bios: LENOVO v: N1EET70W (1.43 ) date: 07/12/2017
CPU:       Quad core Intel Core i7-6820HQ (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 3600 MHz 1: 899 MHz 2: 899 MHz 3: 899 MHz 4: 900 MHz 5: 899 MHz 6: 899 MHz
           7: 899 MHz 8: 899 MHz
Graphics:  Card-1: Intel Skylake Integrated Graphics
           Card-2: NVIDIA GM107GLM [Quadro M1000M]
           Display Server: X.Org 1.19.3 driver: nvidia
           Resolution: 1920x1080@60.00hz, 2560x1440@59.95hz, 1920x1080@60.02hz
           GLX Renderer: Quadro M1000M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 375.66
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel Sound: ALSA v: k4.10.0-32-generic
Network:   Card-1: Intel Ethernet Connection (2) I219-LM driver: e1000e
           IF: enp0s31f6 state: up speed: 1000 Mbps duplex: full mac: 50:7b:9d:f2:96:96
           Card-2: Intel Wireless 8260 driver: iwlwifi
           IF: wlp4s0 state: up mac: 44:85:00:f4:8c:33
Drives:    HDD Total Size: 1520.2GB (5.8% used) ID-1: /dev/nvme0n1 model: N/A size: 256.1GB
           ID-2: /dev/sda model: SAMSUNG_MZNLN512 size: 512.1GB
           ID-3: /dev/sdb model: HGST_HTS721010A9 size: 1000.2GB
           ID-4: USB /dev/sdc model: DataTraveler_3.0 size: 7.9GB
Partition: ID-1: / size: 219G used: 11G (6%) fs: ext4 dev: /dev/nvme0n1p4
           ID-2: /home size: 493G used: 57G (13%) fs: ext4 dev: /dev/sdb3
           ID-3: swap-1 size: 17.08GB used: 0.00GB (0%) fs: swap dev: /dev/nvme0n1p3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 65.5C mobo: N/A gpu: 39C
           Fan Speeds (in rpm): cpu: 3773
Info:      Processes: 300 Uptime: 1 min Memory: 2013.6/15773.5MB Client: Shell (bash) inxi: 2.2.35 
```

Nvidia driver version is 375.66, it's the default one packaged with Xubuntu. I haven't tried any other versions yet. It is also activated via Additional Drivers.

---

### Post by scrawn331 on 2017-08-22
Well, it appears to be fixed now. I just reinstalled the same driver and it hasn't crashed and been running at full load for ~3 hours. I did the following:

```

$ sudo apt-get purge nvidia*
$ sudo reboot

```

Then reinstalled Nvidia 375.66 drivers again through Additional Drivers.

Unsure if this is related, but I also fixed this warning I was getting a warning about /usr/lib/nvidia-375/libEGL.so.1 not being a symbolic link. I fixed that as well.

---

### Post by Bashing-om on 2017-08-22
scrawn331; Outstanding !

IRT libEGL.so.1 :

Bug that as of my last update on 16.04 is still affected:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860) <- /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by gordintoronto on 2017-08-23
Interesting: I would have predicted that it was an overheating issue.

---


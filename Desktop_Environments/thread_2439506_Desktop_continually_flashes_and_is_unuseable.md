---
title: "Desktop continually flashes and is unuseable"
date: 2020-03-28
forum: Desktop Environments
---

### Post by dnube on 2020-03-28
Can get to the command line no problem and the server is running fine otherwise. Been like it for a while but not critical as I can do what I need through command. But is annoying not having usable graphical desktop. Seemed to happen during an update several months ago.  Or maybe the display resolution somehow got changed at some point?

Have tried dpkg-reconfigure xserver-xorg but it just returns me to prompt with no menu/configuration process.

Tried X -configure but it returns with a " ... no devices to configure" message.

It is a Radeon RS690 graphic card.

Also, I can't seem to find the xorg.conf file.

Appreciate any pointers.

DaveNL

---

### Post by ajgreeny on 2020-03-28
Show us more information with the output from command ***inxi -FZX***

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by dnube on 2020-03-28
[COLOR=#000000]ajgreeny:
[/COLOR]Not sure this is the output (or format) you are looking for?
```

System:    Host: WEMBLEY-SERVER Kernel: 4.4.0-176-generic x86_64 (64 bit gcc: 5.4.0) Console: tty 1
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: M2A-VM v: 1.XX Bios: Phoenix v: ASUS M2A-VM 1001 date: 07/16/2007
CPU:       Dual core AMD Athlon 64 X2 4200+ (-MCP-) cache: 1024 KB flags: (lm nx sse sse2 sse3 svm) bmips: 4000 
           clock speeds: max: 2200 MHz 1: 1000 MHz 2: 1000 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS690 [Radeon X1200] bus-ID: 01:05.0
           Display Server: X.org 1.18.4 drivers: fbdev,ati,vesa,vmware,radeon,nouveau,intel,amdgpu
           tty size: 210x65 Advanced Data: N/A for root out of X
Audio:     Card Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA) driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.4.0-176-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: ee00 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 2000.4GB (1.5% used) ID-1: /dev/sda model: ST32000542AS size: 2000.4GB temp: 27C
Partition: ID-1: / size: 1.8T used: 27G (2%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 472M used: 118M (27%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 2.01GB used: 0.00GB (0%) fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 16.0C mobo: 27.0C
           Fan Speeds (in rpm): cpu: 3260 psu: 0 sys-1: 0
Info:      Processes: 189 Uptime: 7:23 Memory: 540.3/1872.9MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (sudo) inxi: 2.2.35 


```

---

### Post by ajgreeny on 2020-03-29
Mea culpa!

Sorry, my command suggestion was a typo - too many upper-case letters in the options shown.
Try```
inxi -Fzx
```
It will give us much more useful info.

It looks as if you are using 16.04 as the kernel version showing was from that version and I wonder if a more recent version might work better with your hardware.  The ***inxi*** output may give us more clues.

---

### Post by jeremy31 on 2020-03-29
> **ajgreeny said:**
> Mea culpa!

Sorry, my command suggestion was a typo - too many upper-case letters in the options shown.
Try```
inxi -Fzx
```
It will give us much more useful info.

It looks as if you are using 16.04 as the kernel version showing was from that version and I wonder if a more recent version might work better with your hardware.  The ***inxi*** output may give us more clues.

That was just the color codes from inxi results, using the c0 will eliminate them
```
inxi -Fxzc0
```

---

### Post by deadflowr on 2020-03-29
> Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS690 [Radeon X1200] bus-ID: 01:05.0
           Display Server: X.org 1.18.4 drivers: fbdev,ati,vesa,vmware,radeon,nouveau,intel,amdgpu
           tty size: 210x65 Advanced Data: N/A for root out of X
Not running a graphical session.
Looks like it was run from a console.
Running from a graphically terminal window, without root or sudo would help.

---


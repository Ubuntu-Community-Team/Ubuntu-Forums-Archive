---
title: "Complete Freeze ubuntu 14.04"
date: 2015-10-19
forum: Desktop Environments
---

### Post by Mago Nick on 2015-10-19
Hello everybody,
I am experiencing an odd problem.
After a while of using my desktop computer it freezes completely. I have  found no solution but to use the reset button on the case.
The thing that makes it hard to track is that is seems to be completely random.
I do not even know where to look to find some information.
I will start with some basic info 

lsb_release -a

```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

```


**uname -a**

```

Linux andrea-workstation 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

**lspci**
```

00:00.0 Host bridge: Intel Corporation Haswell-E DMI2 (rev 02)
00:01.0 PCI bridge: Intel Corporation Haswell-E PCI Express Root Port 1 (rev 02)
00:01.1 PCI bridge: Intel Corporation Haswell-E PCI Express Root Port 1 (rev 02)
00:02.0 PCI bridge: Intel Corporation Haswell-E PCI Express Root Port 2 (rev 02)
00:03.0 PCI bridge: Intel Corporation Haswell-E PCI Express Root Port 3 (rev 02)
00:05.0 System peripheral: Intel Corporation Haswell-E Address Map, VTd_Misc, System Management (rev 02)
00:05.1 System peripheral: Intel Corporation Haswell-E Hot Plug (rev 02)
00:05.2 System peripheral: Intel Corporation Haswell-E RAS, Control Status and Global Errors (rev 02)
00:05.4 PIC: Intel Corporation Haswell-E I/O Apic (rev 02)
00:11.0 Unassigned class [ff00]: Intel Corporation Wellsburg SPSR (rev 05)
00:14.0 USB controller: Intel Corporation Wellsburg USB xHCI Host Controller (rev 05)
00:16.0 Communication controller: Intel Corporation Wellsburg MEI Controller #1 (rev 05)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V (rev 05)
00:1a.0 USB controller: Intel Corporation Wellsburg USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Wellsburg HD Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Wellsburg PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation Wellsburg PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation Wellsburg PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation Wellsburg USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Wellsburg LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Wellsburg 6-Port SATA Controller [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation Wellsburg SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 17c8 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fb0 (rev a1)
06:00.0 PCI bridge: ASMedia Technology Inc. Device 118f
07:01.0 PCI bridge: ASMedia Technology Inc. Device 118f
07:02.0 PCI bridge: ASMedia Technology Inc. Device 118f
07:03.0 PCI bridge: ASMedia Technology Inc. Device 118f
07:04.0 PCI bridge: ASMedia Technology Inc. Device 118f
0c:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
ff:0b.0 System peripheral: Intel Corporation Haswell-E R3 QPI Link 0 & 1 Monitoring (rev 02)
ff:0b.1 Performance counters: Intel Corporation Haswell-E R3 QPI Link 0 & 1 Monitoring (rev 02)
ff:0b.2 Performance counters: Intel Corporation Haswell-E R3 QPI Link 0 & 1 Monitoring (rev 02)
ff:0c.0 System peripheral: Intel Corporation Haswell-E Unicast Registers (rev 02)
ff:0c.1 System peripheral: Intel Corporation Haswell-E Unicast Registers (rev 02)
ff:0c.2 System peripheral: Intel Corporation Haswell-E Unicast Registers (rev 02)
ff:0c.3 System peripheral: Intel Corporation Haswell-E Unicast Registers (rev 02)
ff:0c.4 System peripheral: Intel Corporation Haswell-E Unicast Registers (rev 02)
ff:0c.5 System peripheral: Intel Corporation Haswell-E Unicast Registers (rev 02)
ff:0f.0 System peripheral: Intel Corporation Haswell-E Buffered Ring Agent (rev 02)
ff:0f.1 System peripheral: Intel Corporation Haswell-E Buffered Ring Agent (rev 02)
ff:0f.4 System peripheral: Intel Corporation Haswell-E System Address Decoder & Broadcast Registers (rev 02)
ff:0f.5 System peripheral: Intel Corporation Haswell-E System Address Decoder & Broadcast Registers (rev 02)
ff:0f.6 System peripheral: Intel Corporation Haswell-E System Address Decoder & Broadcast Registers (rev 02)
ff:10.0 System peripheral: Intel Corporation Haswell-E PCIe Ring Interface (rev 02)
ff:10.1 Performance counters: Intel Corporation Haswell-E PCIe Ring Interface (rev 02)
ff:10.5 System peripheral: Intel Corporation Haswell-E Scratchpad & Semaphore Registers (rev 02)
ff:10.6 Performance counters: Intel Corporation Haswell-E Scratchpad & Semaphore Registers (rev 02)
ff:10.7 System peripheral: Intel Corporation Haswell-E Scratchpad & Semaphore Registers (rev 02)
ff:12.0 System peripheral: Intel Corporation Haswell-E Home Agent 0 (rev 02)
ff:12.1 Performance counters: Intel Corporation Haswell-E Home Agent 0 (rev 02)
ff:13.0 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Target Address, Thermal & RAS Registers (rev 02)
ff:13.1 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Target Address, Thermal & RAS Registers (rev 02)
ff:13.2 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder (rev 02)
ff:13.3 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder (rev 02)
ff:13.4 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder (rev 02)
ff:13.5 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel Target Address Decoder (rev 02)
ff:13.6 System peripheral: Intel Corporation Haswell-E DDRIO Channel 0/1 Broadcast (rev 02)
ff:13.7 System peripheral: Intel Corporation Haswell-E DDRIO Global Broadcast (rev 02)
ff:14.0 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 0 Thermal Control (rev 02)
ff:14.1 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 1 Thermal Control (rev 02)
ff:14.2 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 0 ERROR Registers (rev 02)
ff:14.3 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 1 ERROR Registers (rev 02)
ff:14.6 System peripheral: Intel Corporation Haswell-E DDRIO (VMSE) 0 & 1 (rev 02)
ff:14.7 System peripheral: Intel Corporation Haswell-E DDRIO (VMSE) 0 & 1 (rev 02)
ff:15.0 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 2 Thermal Control (rev 02)
ff:15.1 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 3 Thermal Control (rev 02)
ff:15.2 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 2 ERROR Registers (rev 02)
ff:15.3 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 0 Channel 3 ERROR Registers (rev 02)
ff:16.0 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 1 Target Address, Thermal & RAS Registers (rev 02)
ff:16.6 System peripheral: Intel Corporation Haswell-E DDRIO Channel 2/3 Broadcast (rev 02)
ff:16.7 System peripheral: Intel Corporation Haswell-E DDRIO Global Broadcast (rev 02)
ff:17.0 System peripheral: Intel Corporation Haswell-E Integrated Memory Controller 1 Channel 0 Thermal Control (rev 02)
ff:17.4 System peripheral: Intel Corporation Haswell-E DDRIO (VMSE) 2 & 3 (rev 02)
ff:17.5 System peripheral: Intel Corporation Haswell-E DDRIO (VMSE) 2 & 3 (rev 02)
ff:17.6 System peripheral: Intel Corporation Haswell-E DDRIO (VMSE) 2 & 3 (rev 02)
ff:17.7 System peripheral: Intel Corporation Haswell-E DDRIO (VMSE) 2 & 3 (rev 02)
ff:1e.0 System peripheral: Intel Corporation Haswell-E Power Control Unit (rev 02)
ff:1e.1 System peripheral: Intel Corporation Haswell-E Power Control Unit (rev 02)
ff:1e.2 System peripheral: Intel Corporation Haswell-E Power Control Unit (rev 02)
ff:1e.3 System peripheral: Intel Corporation Haswell-E Power Control Unit (rev 02)
ff:1e.4 System peripheral: Intel Corporation Haswell-E Power Control Unit (rev 02)
ff:1f.0 System peripheral: Intel Corporation Haswell-E VCU (rev 02)
ff:1f.2 System peripheral: Intel Corporation Haswell-E VCU (rev 02)

```

Since I know from experience that nvidia drivers may causes problem here some info about them



**dpkg -l | grep nvidia**
```

ii  nvidia-352                                            352.39-0ubuntu1                                     amd64        NVIDIA binary driver - version 352.39
ii  nvidia-352-dev                                        352.39-0ubuntu1                                     amd64        NVIDIA binary Xorg driver development files
ii  nvidia-352-uvm                                        352.39-0ubuntu1                                     amd64        Transitional package for nvidia-352
ii  nvidia-modprobe                                       352.39-0ubuntu1                                     amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-opencl-icd-352                                 352.39-0ubuntu1                                     amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       352.39-0ubuntu1                                     amd64        Tool for configuring the NVIDIA graphics driver

```


I am using the cuda version downloaded from the website.

Well, I do not know what other info to post. In case you need something 
else just ask that I will provide you the info by modifying this initial
 post.

Thank you very much!

Andrea

EDIT: 
Some additional info

[B]head /proc/meminfo



[/B]```
MemTotal:       32848732 kB

MemFree:        29910436 kB

MemAvailable:   30962636 kB

Buffers:           87384 kB

Cached:          1144984 kB

SwapCached:            0 kB

Active:          2005888 kB

Inactive:         636344 kB

Active(anon):    1411404 kB

Inactive(anon):    48372 kB


```[B]







free -m[/B]



```


             total       used       free     shared    buffers     cached

Mem:         32078       2871      29207         48         85       1118

-/+ buffers/cache:       1667      30411

Swap:        61033          0      61033




```

EDIT: more logs
**Xorg.0.log:** [http://pastebin.com/tyunvemq](http://pastebin.com/tyunvemq)

**pm-powersave.log:** [http://pastebin.com/JVi3w2kY](http://pastebin.com/JVi3w2kY)

**kern.log:** [http://pastebin.com/12WTjjzi](http://pastebin.com/12WTjjzi)

**lightdm.log: **  [http://pastebin.com/Q7yK6Eg5](http://pastebin.com/Q7yK6Eg5)[URL="http://pastebin.com/Q7yK6Eg5"]
[/URL]

---

### Post by TheFu on 2015-10-19
Ok. 

First question - is this a GUI issue only?  Can you connect to the system via **ssh** over the network? A GUI lockup happens much more often than a complete OS lockup. Troubleshooting is different.

Also, what does **dmesg** and the **syslog** show? The trick to access these post-lock-up is to boot off alternate media, mount the /var/log storage and view the files without booting the installed OS.

---

### Post by Mago Nick on 2015-10-19
Hi,
Thank for your fast response. It seems to be a full OS freeze. I was listening to some audio when it freezed and also the audio stopped. I did not do how you suggested, as soon as it freezes again I will save the logs.

---

### Post by Mago Nick on 2015-10-22
Hi, 
Since the problem showed up twice today I had the occasion to gather the information you have asked. I added in the first post so it easy to find them for the other users. 
thank you
Andrea

---

### Post by TheFu on 2015-10-22
Thanks.

I don't see anything wrong in those files. That's good and bad. Good because some hardware doesn't seem to be breaking.  Bad because we have to guess at answers.

If you are willing to post more data, I've created a system info gathering script. [http://blog.jdpfu.com/sysinfo](http://blog.jdpfu.com/sysinfo) Just post the URL created.  Mainly want to know the amount of RAM and swap use.  I found on a low-RAM system that lockups happened due to out-of-RAM situations.  By increasing the swap partition, those lockups all stopped. Completely.

---

### Post by Mago Nick on 2015-10-22
Hi the link does not seem to work. 
The ram is 32GB and the Swap in use is 0. 
If you would like me to execute any command to gather info, I am here.

Probably is not really related to the desktop environment as I thought. Should this conversation be moved in a more appropriate place?

---

### Post by TheFu on 2015-10-22
0 swap?   On a desktop?  Don't think I'd do that. 32G?   Really?  None of my servers have that much RAM, but we don't run windows or geospatial DBs either.

$ head  /proc/meminfo
$  free  -m
Please post the output from those cmds. I'd be really surprised if more than 4G were used.

BTW, my last "desktop" build cost US$146 and easily runs multiple VMs. 

Also checked the reverse-proxy logs. Doesn't appear that anyone hit the link today besides YandexBot. Can you tell if it is a DNS or routing issue?  I know that some less-than-open governments have decided to block my little Linux blog.  Don't know why.  I only complain about my government ;) and there isn't any offensive words on there that I know.

---

### Post by Mago Nick on 2015-10-22
I am a researcher in robotics vision, that's why of so much RAM.

I am afraid I made a mistake there are more than 60GB of Swap.

Follow the outputs of the commands you asked

[B]head /proc/meminfo

[/B]```
MemTotal:       32848732 kB
MemFree:        29910436 kB
MemAvailable:   30962636 kB
Buffers:           87384 kB
Cached:          1144984 kB
SwapCached:            0 kB
Active:          2005888 kB
Inactive:         636344 kB
Active(anon):    1411404 kB
Inactive(anon):    48372 kB

```[B]



free -m[/B]

```

             total       used       free     shared    buffers     cached
Mem:         32078       2871      29207         48         85       1118
-/+ buffers/cache:       1667      30411
Swap:        61033          0      61033


```

---

### Post by TheFu on 2015-10-22
While not likely an issue, that is a bunch of memory (combined  RAM/swap) for a desktop. Under 3G used. Any GUI programs being used that monitors memory use?  Do you have any monitoring setup like monit or munin that could show issues just prior to the crash?

Any warnings or errors in other log files? Just grep.

---

### Post by Mago Nick on 2015-10-23
HI,
The only application that gives me some information about the system is the Xfce4 applet "xfce4-systemload-plugin 1.1.1".

I checked the log, but I did not find anything strange. Since I might be  wrong I attach them. I had to upload on pastebin since they were to big  to either be pasted on a message or to be uploaded as attachment.



**Xorg.0.log:** [http://pastebin.com/tyunvemq](http://pastebin.com/tyunvemq)

**pm-powersave.log:** [http://pastebin.com/JVi3w2kY](http://pastebin.com/JVi3w2kY)

**kern.log:** [http://pastebin.com/12WTjjzi](http://pastebin.com/12WTjjzi)

**lightdm.log: **  [URL="http://pastebin.com/Q7yK6Eg5"]http://pastebin.com/Q7yK6Eg5
[/URL]

By mistake I have edited wrong the first post, is there any way to retrieve the old post? I have been working far too many hours ](*,)

EDIT: recovered first post, thank you google cache

---

### Post by Mago Nick on 2015-10-24
It happened twice today. I am running out of ideas.

---

### Post by Mago Nick on 2015-10-27
A small update.

The situation was getting worse and worse so I tried a fresh install of Ubuntu 14.04, downloaded from the official website.

It did not solve the issue. However, now I can track the problem a bit more. In fact, it appears every time I run a ros-based (see [www.ros.org](www.ros.org)) and openCV application. Is systematic, every time I run it the system completely freeze.

The code is not mine, but among all the users I am the only one that is having this problem. 

Might this be caused by the nvidia drivers?

---

### Post by Mago Nick on 2015-10-28
I have found this thread [http://ubuntuforums.org/showthread.php?t=2257257](http://ubuntuforums.org/showthread.php?t=2257257) that seems to address my problem, I disable the option, but it keeps freezing, I will run a memtest during the night to see what happens. 
Any suggestion is welcome,
Andrea

---

### Post by poorguy on 2015-11-08
i am having the same problem. my desktop will just lockup and the only fix is a hard restart. ubuntu mate 14.04 LTS 64bit. / core 2 duo e6400 / 3.0 gb ddr2 / nvidia 7300 le pcie / hp- pavilion d4650y . tried all of the nvidia proprietary drivers which makes it worse so back to open source driver.

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 LE] (rev a1)
03:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) Video Decoder (rev 01)
03:01.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
03:04.0 Ethernet controller: Qualcomm Atheros AR5413/AR5414 Wireless Network Adapter [AR5006X(S) 802.11abg] (rev 01)MemTotal:        3080480 kB

MemFree:         2060680 kB
MemAvailable:    2475644 kB
Buffers:           85304 kB
Cached:           441024 kB
SwapCached:            0 kB
Active:           696912 kB
Inactive:         191260 kB
Active(anon):     362832 kB
Inactive(anon):    11244 kB

nouveau              1206535  2 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  1 nouveau
ttm                    93588  1 nouveau
drm_kms_helper         61574  1 nouveau
drm                   311018  5 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13413  2 ivtv,nouveau

thanks

---

### Post by Mago Nick on 2015-11-09
Hi, 
actually my pc froze also during the memtest run on parallel on all the 12 cores. I had the suspect of faulty hardware and I had the computer sent back to the customer care. Apparently that solved the problem. I am waiting for the complete report of the repair to have it confirmed, though. If nothing happens until friday I will mark the question solved.
**@Poorguy: **About your case. I suggest you to open a new discussion and add infos gathered from the logs as well. 
Thanks 
Andrea

---


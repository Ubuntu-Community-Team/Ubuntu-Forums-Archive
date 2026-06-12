---
title: "Changing Home Directory Size &amp; Installing Audio"
date: 2005-01-25
forum: Desktop Environments
---

### Post by derdewey on 2005-01-25
Hi, I'm loving Ubuntu but I've got two problems that my searching hasn't been able to fix.

1) My /home/ directory is limited to a measly 300mb and I don't know how to edit that... not only that, I don't even know how to phrase this question for search engines!

2) I've got a MSI K8N Neo2 motherboard and I want to use it's integrated sound... I downloaded the nvidia binaries but when I run that it just tells me that it doesn't support this operating system.  Any ideas on how to install the drivers for a Realtek ALC850 AC97 codec?  Suse 9.1 saw it...  hehe, then again, Suse 9.1 didn't see my network adapter!

---

### Post by matid on 2005-01-25
1. Is /home different from partition mounted at / ?

---

### Post by nocturn on 2005-01-25
[QUOTE=derdewey]Hi, I'm loving Ubuntu but I've got two problems that my searching hasn't been able to fix.

1) My /home/ directory is limited to a measly 300mb and I don't know how to edit that... not only that, I don't even know how to phrase this question for search engines!

2) I've got a MSI K8N Neo2 motherboard and I want to use it's integrated sound... I downloaded the nvidia binaries but when I run that it just tells me that it doesn't support this operating system.  Any ideas on how to install the drivers for a Realtek ALC850 AC97 codec?  Suse 9.1 saw it...  hehe, then again, Suse 9.1 didn't see my network adapter![/QUOTE]

1)  Can you post the output of the command 'df -m' (run in terminal)

2) I think those binaries are for Windows only...  Can you use sudo lspci to see if your card is listed?

---

### Post by derdewey on 2005-01-25
[QUOTE=nocturn]1)  Can you post the output of the command 'df -m' (run in terminal)

2) I think those binaries are for Windows only...  Can you use sudo lspci to see if your card is listed?[/QUOTE]

For the df -m command I got this...
```

 Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda3                14084      1749     11620  14% /
tmpfs                      501         0       501   0% /dev/shm

```

and for the lspci I got this...
```

0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00e a (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 00ee (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Rad eon 9500 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 P ro] (Secondary)
0000:02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 46)
0000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigab it Ethernet (rev 10)

```

How shakey is 64bit support on Ubuntu?  When I try to update to hoary is says that the x86_64 packages aren't there.  Just curious, things are running nicely now.  Thanks for the help folks!

---


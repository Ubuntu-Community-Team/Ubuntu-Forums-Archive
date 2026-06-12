---
title: "ATI 8.29.6 and 2.6.18 kernel is it possible ??"
date: 2006-09-21
forum: Desktop Environments
---

### Post by tworkemon on 2006-09-21
Hello,

Based on ATI changelog it is possible but I am having problems doing the above. I was wondering if anyone has been able to successfully have both ;) I did notice an issue with module-assistant and backporting from edgy help some but im still failing to accomplish the above. I will post errors later when I get home, just thought I would put this out there to see if anyone else has tried.

---

### Post by tworkemon on 2006-09-21
Well, After going home and trying one more time. I found it is possible. The only thing that is needed is to backport or replace your module-assistant with the edgy one. I just went into the package list and downloaded the file. Probably not the best way and of course backup yours in case if something else breaks :P .

---

### Post by Keenn on 2006-09-22
it's not working for me. fglrx built successfully, but its still not working.

```

keenn@keenn:~$ dmesg | grep fglrx
[  110.543913] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[  110.544178] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on minor 0
[  111.737655] [fglrx] Internal AGP is not supported in 2.6 kernel.
[  111.738032] [fglrx:firegl_unlock] *ERROR* Process 6803 using kernel context 0

```

6803 is my X server.

this is warnings from Xorg.0.log:

```

keenn@keenn:~$ cat /var/log/Xorg.0.log | grep fglrx | grep WW
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): GetVBEMode failed
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

```

i had same problem on edgy with 2.6.17-7 kernel. now i'm in dapper on 2.6.18. my video is X800PRO AGP.

---

### Post by tworkemon on 2006-09-23
First off make sure it compiled with the correct kernel headers. Second try this.
> sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
reboot.

When you are running those commands make sure you see it picking up the 2.6.18 kernel

Also try to replace the current xorg.conf file with your back up ;) that is if you made one. I had a similar problem and it was just bad configuration of the xorg.conf file.

If all else fails I would remove any fglrx from adept and xorg-driver-fglrx and reinstall the drivers. Do this prior to reinstalling the drivers.

> sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa

Im leaning towards bad configuration of your xorg.conf file.

---


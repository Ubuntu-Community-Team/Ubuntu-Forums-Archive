---
title: "How to Install Feisty (7.04) on Insipron 1521"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by Drchoc on 2007-08-07
Hello this is a guide written for those of you with an Insprion 1521, or similar hardware.

Inspiron 1521 
ATi X1270
Broadcom 1390 WLAN
1521 Sound

Okay lets begin first thing is first there are two ways of installing Feisty. 
[LIST]
[*]live CD install- Go to the section on ATI driver install, but don't reboot.
[*]Alternate- This is the text version just follow the onscreen directions
[/LIST]

**_Get ATI Working_**

For getting ATI working please refer here.
[Fix ATi]("http://ubuntuforums.org/showthread.php?t=414194")

**_Get WiFi Working_**

For the wireless drivers please Refer to this thread. [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

**_Finally Getting Sound Working_**

To get sound to work first download the file *804.tar.bz

[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)

From there install the drivers and select alsa-firmware on synaptic

To install the drivers unzip then 
```
./hgcompile
sudo make install
```

**Note:**
None of these solutions were made by me and I no credit I'm just linking them in one spot were others can easily find it.

---

### Post by lift28 on 2007-12-18
For Gutsy 7.10

unit is 64bit dual - ati video

Hook up to the wired lan

wireless - enable restricted driver and reboot (brodcom43xx)- i use wlassistant, i do a lot of hopping around, this works better then the default app for me.

ATI video - enable restricted driver and reboot (video vga out not working) (enable at same time as wifi)

boot splash on this page: [http://www.ubuntu1501.com/2007/11/fix-for-gutst-taking-forever-to.html](http://www.ubuntu1501.com/2007/11/fix-for-gutst-taking-forever-to.html)

Sound - not sure if it was  the first command or second - sorry : sudo apt-get install linux-backports-modules-generic or/and sudo apt-get remove alsa  - i also installed a few other things: sudo apt-get install alsamixergui alsa-tools alsa-tools-gui alsa-oss alsaplayer-alsa  (mic works setup in alsa config )

Note:
None of these solutions were made by me and I no credit I'm just linking them in one spot were others can easily find it.

---


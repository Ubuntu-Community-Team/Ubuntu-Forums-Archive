---
title: "Webcam Problem - Log File"
date: 2014-04-27
forum: Desktop Environments
---

### Post by Geoff_Lane on 2014-04-27
Folks,

Ubuntu 14.04 Built in webcam problem

I recently posted a similar message as shown below but now include log files.

[http://ubuntuforums.org/showthread.php?t=2218371](http://ubuntuforums.org/showthread.php?t=2218371)

This is not my computer, I am in the UK and my friend lives in US, she had an earlier version of Ubuntu but upgraded online to 14.04.

The laptop's built in webcam still does not work.

An edited dmesg and lsmod is shown below;

```


dmesg

0.539084] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cefff])
0.765265] pci 0000:00:01.0: Boot video device
 14.647877] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.694627] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   14.711703] acer_wmi: Brightness must be controlled by acpi video driver
[  291.368607] Linux video capture interface: v2.00
[  291.462781] usbcore: registered new interface driver uvcvideo
[  291.462786] USB Video Class driver (1.1.1)
```

```
lsmod

uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
video                  18903  1 acer_wmi
```

Cheese says no device found.

I can access the computer via ssh to her terminal or VNC and would appreciate any advice as to what to try next.

Geoff Lane

---


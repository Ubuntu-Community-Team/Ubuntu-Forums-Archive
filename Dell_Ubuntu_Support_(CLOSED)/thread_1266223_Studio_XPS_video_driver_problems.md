---
title: "Studio XPS video driver problems"
date: 2009-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BigCdaAnswer3 on 2009-09-14
Hey all, I recently purchased a new Dell Studio XPS laptop. I need to have Ubuntu 8.04 installed for work/development purposes, so I proceeded to do a normal, cd-based install. Upon booting into my newly installed OS, I saw the restricted drivers manager in the toolbar, so I opened it up and saw that there was a proprietary driver needed for the NVIDIA graphics card (9400m), so I enabled it. After rebooting, I get no tty's and no X server. Relevant Xorg.0.log output:

(II) NVIDIA(0): Initialized GPU GART.
(WW) NVIDIA(0): Error: Unable to find DOS (Enable/Disable output switching)
(WW) NVIDIA(0):     file path under /proc/acpi/video. NVIDIA X driver will not
(WW) NVIDIA(0):     be able to respond to  display change hotkey events.
(II) NVIDIA(0): Setting mode "800x600@60"

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7eea420]

Fatal server error:
Caught signal 8.  Server aborting


I'm fairly certain that this laptop will work with newer versions of ubuntu, but I need it to work with hardy...can anyone suggest a particular nvidia driver version/configuration that could work here??? Much appreciation in advance!!

---

### Post by coffeeaddict22 on 2009-09-15
Hi,
The easy answer is to do without the proprietary driver.  The FOSS driver is getting better, although I think with NVIDIA you'll still miss out on some of the whizzbang stuff.
8.04 is an LTS, so your card should work.  Have a look through the output of the logs in System/Administration/Log file viewer, or (if you like terminals) in the log files at /var/log; dmesg is the best one for the big picture, and you can usually go from there, although with a display problem /var/log/Xorg.O.log would be a pretty close second.

---

### Post by BigCdaAnswer3 on 2009-09-15
coffeeaddict22, thanks for the reply. it's been awhile since i've had an nvidia card, which driver package do i need to install for the foss nvidia driver? i really don't need to do any whizbang stuff like compiz, i just need it to support XGA resolution, the highest i got with the vesa driver was 800x600

---

### Post by Heroshinator on 2009-09-15
Look into a program called Envy it should help you install the video card driver you need. Really simplifies the process.

---

### Post by superm1 on 2009-09-15
You need a newer NVIDIA driver than that that ships with 8.04.  Either install a more recent version of Ubuntu (9.04), or grab the newer driver from NVIDIA's website and install it.

---


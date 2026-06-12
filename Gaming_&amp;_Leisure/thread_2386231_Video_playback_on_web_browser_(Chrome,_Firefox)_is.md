---
title: "Video playback on web browser (Chrome, Firefox) is stuttering"
date: 2018-03-02
forum: Gaming &amp; Leisure
---

### Post by matheusr98 on 2018-03-02
Hello Ubuntu users, i've been having some issues on my PC lately. The hardware is:


- CPU: Intel Core 2 Quad Q6600  2.4GHz (OC to 3.0GHz)- Revision B0 (using intel-microcode driver);
- RAM: 3GB of DDR2 800Mhz - (OC to 1066MHz);
- HDD: 1 Seagate 500GB - 1 Samsung HDD 150GB - 1 Samsung HDD 80GB, all of them been SATA;
- GPU: NVidia GeForce 9500GT - 512MB DDR3 VRAM (using NVidia 340.104 close-sourced drivers);


This is a old PC that i've build a long time ago, and I wasn't using it. I've installed Windows 7 back in 2010, and in 2011, it was time for Ubuntu 11.10. But after around Ubuntu 17.04, and specially now, with Ubuntu 17.10, I started noticing that for some reason, when I'm watching a YouTube video or even a Twitch livestream and the video is not in fullscreen, after every 2 second of video playing back normally, it stutters for like, half of a second, and then it plays as it should. But then it repeats. Does anyone else have this problem? Can I solve it?

---

### Post by SeijiSensei on 2018-03-02
For Flash videos, make one full-screen then right-click on the image.  Do you have hardware acceleration enabled?  If not, give that a try.

---

### Post by bananafishbones on 2018-03-20
I hate to hijack a thread but this post is fairly new and I'm having the exact same issue. I have the NVIDIA drivers installed and running.

How can we test to ensure hardware acceleration is working? I'm fairly confident it is as prior to installing the NVIDIA drivers, graphics were slow and response times were off but that is no longer the case.

I'm experiencing stuttering in both Chrome and Firefox when playing Youtube content on either monitor (different resolutions)

 OS: Ubuntu 17.10 x86_64
 Host: Precision 5820 Tower
 Kernel: 4.13.0-36-generic
 Resolution: 1920x1080, 3840x2160
 DE: ubuntu:GNOME
 WM: GNOME Shell
 WM Theme: Arc-Dark
 CPU: Intel Xeon W-2102 (4) @ 2.900GHz
 GPU: NVIDIA Quadro P1000
 Memory: 11816MiB / 31840MiB

---

### Post by tinylagarto on 2018-03-20
As I remember 17.10 defaults to Wayland. Maybe if you change back to xorg from the login screen you could see an improvement. Just an idea.

---

### Post by bananafishbones on 2018-03-21
Thanks Ivan,

Per echo $DESKTOP_SESSION I'm running ubuntu-xorg.

---

### Post by tinylagarto on 2018-03-21
Maybe we should see the settings in Firefox, if hardware acceleration is enabled. On my Intel card I have to force it. 

Could you open *about:support* in Firefox? Then find the section with HW_COMPOSITING. It should say if is enabled or disabled. 

In Chrome it is *chrome://gpu*, or typing *about:gpu*.

---

### Post by bananafishbones on 2018-03-21
Graphics Feature Status
Canvas: Hardware accelerated
CheckerImaging: Disabled
Flash: Hardware accelerated
Flash Stage3D: Hardware accelerated
Flash Stage3D Baseline profile: Hardware accelerated
Compositing: Hardware accelerated
Multiple Raster Threads: Enabled
Native GpuMemoryBuffers: Software only. Hardware acceleration disabled
Rasterization: Software only. Hardware acceleration disabled
Video Decode: Software only, hardware acceleration unavailable
WebGL: Hardware accelerated
WebGL2: Hardware accelerated

---

### Post by tinylagarto on 2018-03-21
In Chrome I have the same output but no problems. 
Though with Gnome Shell sometimes I also had similar problems, not sure if it is Mutter or the graphics card.

---

### Post by bananafishbones on 2018-03-28
> **ivanovnegro2 said:**
> In Chrome I have the same output but no problems. 
Though with Gnome Shell sometimes I also had similar problems, not sure if it is Mutter or the graphics card.

I'll investigate further and post my findings here.

Thank you for your assistance Ivan and Seij!

---


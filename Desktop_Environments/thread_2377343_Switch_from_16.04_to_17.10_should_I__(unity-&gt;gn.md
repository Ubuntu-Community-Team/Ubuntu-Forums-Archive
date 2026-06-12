---
title: "Switch from 16.04 to 17.10 should I ? (unity-&gt;gnome transition)"
date: 2017-11-12
forum: Desktop Environments
---

### Post by thehannibal on 2017-11-12
I'm starting this thread for NEW USERS like me [[IMG]https://ubuntuforums.org/images/icons/icon6.png[/IMG]], who have switched to Ubuntu (<6 months) recently and don't know whether to switch to Gnome. I had Windows 10 previously but to avoid the hassle of installing Cygwin and emulating bash ie: gnome-terminal, I entirely switched to Ubuntu. I have like Ubuntu 16.04 so far and it's interactions are good, Boot Up times are flawless, switching between windows is fast. Sublime, Pycharm and Clion work smooth. Firefox is snappy. And the thing I most like is that in UNITY, the Menu Bar + Title Bar + Unity Panel = just the Unity Panel, that is to say they they have a seamless Integration and Drop down menu's are good. See how the title bar changes to menu bar in the maximized window (Nemo FM) in image below:

[https://uploads.disquscdn.com/images/f60c97a9d5a3bf4ee52c20c968347f0a0b1a7fe4a62729d7869fa2cf1363ce91.png](https://uploads.disquscdn.com/images/f60c97a9d5a3bf4ee52c20c968347f0a0b1a7fe4a62729d7869fa2cf1363ce91.png)

[https://uploads.disquscdn.com/images/ad6cd326d41898f2904b964ac8082f49323b6eaaafd239a47d8d29622e4d24ba.png](https://uploads.disquscdn.com/images/ad6cd326d41898f2904b964ac8082f49323b6eaaafd239a47d8d29622e4d24ba.png)

Please help me decide whether I should stick with 16.04 as I like Unity, or should I switch to 17.10 or wait for upcoming 18.04. Will gnome desktop be as good and smooth as Unity ? I have just started using Ubuntu and have never used Gnome, maybe Gnome is faster and snappier do tell. What are the PRO's and CON's of switching to newer Ubuntu if I may. Thanks.

---

### Post by westie457 on 2017-11-12
Hi, for stability I would stay with 16.04 LTS.
Just looking and exploring 17.10 I would try a virtual machine or only as a live USB.

---

### Post by vasa1 on 2017-11-12
> **westie457 said:**
> Hi, for stability I would stay with 16.04 LTS.
Just looking and exploring 17.10 I would try a virtual machine or only as a live USB.
+1 a thousand times! That's what I'm doing as well.

You could also tell us something about your system. If you don't have *inxi* installed, please install it from the software center or by using *apt-get*. If it isn't available you may need to enable the Universe repository first and then update your system. After that, run```
inxi -Fxzc0
```and post the output here. The output may help people guide you better.

---

### Post by thehannibal on 2017-11-12
Limited Internet where I work from, I would like to give 17.10 a try, but before that can somebody post few screenshots of how their 17.10 looks like after modifications for productivity (I mean you have selected your preferred theme and applied it, switched the Launcher to bottom, adjusted the transparency), please don't point me to fresh install screenshots as I know what they would look like. Mainly, can somebody post these screenshots :

1> Firefox when maximized with Launcher at bottom, it's title bar, menu bar, drop down menu.
2> Sublime when maximized and title/menu bar transition, it's drop down menu.
3> The application search when you press Win button (fullscreen).
4> Maybe how your File Manager (I like Nemo) looks.

Thanks, with just few screenshots from 5-6 experienced and Veteran users who have heavily modified Ubuntu 17.10 to look good and snappy for productivity I will be able to know what my 17.10 would look like after 1-3 weeks of use and whether gnome is worth it or not.

---

### Post by thehannibal on 2017-11-12
```
lucifer@Orpheus:~$ inxi -Fxzc0
System:    Host: Orpheus Kernel: 4.10.0-38-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9) Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire V5-573G
           Mobo: Acer model: Dazzle_HW v: Type2 - A01 Board Version
           Bios: Insyde v: V2.28 date: 04/16/2014
CPU:       Dual core Intel Core i7-4500U (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9578
           clock speeds: max: 3000 MHz 1: 800 MHz 2: 967 MHz 3: 806 MHz
           4: 857 MHz
Graphics:  Card-1: Intel Haswell-ULT Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: NVIDIA GK107M [GeForce GT 750M] bus-ID: 01:00.0
           Display Server: X.Org 1.19.3 drivers: (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1366x768@60.01hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Haswell-ULT HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-38-generic
Network:   Card-1: Qualcomm Atheros AR9462 Wireless Network Adapter
           driver: ath9k bus-ID: 04:00.0
           IF: wlp4s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 4000 bus-ID: 05:00.1
           IF: enp5s0f1 state: down mac: <filter>
Drives:    HDD Total Size: 1000.2GB (35.8% used)
           ID-1: /dev/sda model: WDC_WD10JPVX size: 1000.2GB temp: 39C
Partition: ID-1: / size: 113G used: 9.9G (10%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 8.19GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A gpu: 39.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 208 Uptime: 1:07 Memory: 1644.9/7861.1MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```

---

### Post by vasa1 on 2017-11-12
> **thehannibal said:**
> Limited Internet where I work from, I would like to give 17.10 a try, but before that can somebody post few screenshots of how their 17.10 looks like after modifications for productivity (I mean you have selected your preferred theme and applied it, switched the Launcher to bottom, adjusted the transparency), please don't point me to fresh install screenshots as I know what they would look like. Mainly, can somebody post these screenshots :

1> Firefox when maximized with Launcher at bottom, it's title bar, menu bar, drop down menu.
2> Sublime when maximized and title/menu bar transition, it's drop down menu.
3> The application search when you press Win button (fullscreen).
4> Maybe how your File Manager (I like Nemo) looks.

Thanks, with just few screenshots from 5-6 experienced and Veteran users who have heavily modified Ubuntu 17.10 to look good and snappy for productivity I will be able to know what my 17.10 would look like after 1-3 weeks of use and whether gnome is worth it or not.

Until someone obliges specifically, you can look at recent posts in [Ubuntu/Linux Screenshot Thread]("https://ubuntuforums.org/showthread.php?t=2351238")

---

### Post by thehannibal on 2017-11-12
+1 for Screenshot thread NICE, but NOT EVEN ONE screenshot in the last 6 pages Page 15,14,13,12,11,10 has a **Windows maximized**. Can someone please oblige specifically for my cause.

---

### Post by kurt18947 on 2017-11-12
Here's my 16.04 desktop, 17.10 is nearly identical. I've never used Unity much, stayed with ubuntu-gnome so it's not much of a transition to Ubuntu 17.10. I think of 17.10 as a beta of the next LTS, 18.04. The only problem I've had with 17.10 so far is that it doesn't recognize the Brother MFD scanner. Printer is fine, scanner is not recognized. I'm using Nemo in lieu of the default file manager in 16.04. Nautilus does seem to be better in 17.10. I have the following extensions installed in 16.04:

Dash to Dock - a slightly modified version is used as the launcher in 17.10. I could also install Dash to Dock on 17.10 which would disable the default dock and would give more customization but no official support.
Lock Keys - numlock indicator that sits in the upper right corner. Useful for keyboards without indicators
Open Weather
Suspend Button
No Topleft hot corner - Keeps me from clicking the 'activities' area when trying to click file manager on the dock.
Task Bar - This adds the bottom panel and enables tweaking such as panel color changes.

[ATTACH=CONFIG]277498[/ATTACH]

17.10 is the same with the exception of Dash to Dock. The default works for me so far.

---

### Post by ian-weisser on 2017-11-12
Asking us to help you decide this seems rather pointless.
Download a 17.10 LiveUSB image, try it, and decide for yourself. That's what they are for.

---

### Post by thehannibal on 2017-11-12
> **kurt18947 said:**
> Here's my 16.04 desktop, 17.10 is nearly identical. I've never used Unity much, stayed with ubuntu-gnome so it's not much of a transition to Ubuntu 17.10. I think of 17.10 as a beta of the next LTS, 18.04. The only problem I've had with 17.10 so far is that it doesn't recognize the Brother MFD scanner. Printer is fine, scanner is not recognized. I'm using Nemo in lieu of the default file manager in 16.04. Nautilus does seem to be better in 17.10. I have the following extensions installed in 16.04:

Dash to Dock - a slightly modified version is used as the launcher in 17.10. I could also install Dash to Dock on 17.10 which would disable the default dock and would give more customization but no official support.
Lock Keys - numlock indicator that sits in the upper right corner. Useful for keyboards without indicators
Open Weather
Suspend Button
No Topleft hot corner - Keeps me from clicking the 'activities' area when trying to click file manager on the dock.
Task Bar - This adds the bottom panel and enables tweaking such as panel color changes.

[ATTACH=CONFIG]277498[/ATTACH]

17.10 is the same with the exception of Dash to Dock. The default works for me so far.

Thanks for informing about the scanner problem. I use my office scanner almost every day and it is very important, Till this issue is fixed I won't be trying 17.10. Now I'm going to **stick with 16.04** till 18.04 comes out and then decide whether to switch or not.

---

### Post by thehannibal on 2017-11-12
> **ian-weisser said:**
> Asking us to help you decide this seems rather pointless.
Download a 17.10 LiveUSB image, try it, and decide for yourself. That's what they are for.

The ISO image at [http://mirror.waia.asn.au/ubuntu-releases/17.10/](http://mirror.waia.asn.au/ubuntu-releases/17.10/) is 1.4 GB and my current speed limit is low. I have decided to run 16.04 till 18.04 comes due to scanner issue mentioned.

---


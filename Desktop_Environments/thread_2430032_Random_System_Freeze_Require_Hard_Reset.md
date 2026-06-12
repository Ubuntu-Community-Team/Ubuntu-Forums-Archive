---
title: "Random System Freeze Require Hard Reset"
date: 2019-10-26
forum: Desktop Environments
---

### Post by scpatl4now on 2019-10-26
I have been dealing with this for several months now on 19.04 and now 19.10, and through process of elimination have ruled out the following
Multiple runs of testing memory...no errors
Ran processor stress test...no crash
Its not a problem with over taxing my system since it has never crashed playing games like Cities Skylines through Steam.
Have ruled out electrical problems
I have the latest BIOS (from Sept 24th)
I also tried KDE and plasma desktop same behavior always when Firefox running, so a Gnome specific problem ruled out 
This is my system info:

```

System:
  Host: scott-System-DISCO Kernel: 5.3.0-19-generic x86_64 bits: 64 
  Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Desktop Mobo: ASUSTeK model: PRIME X370-PRO v: Rev X.0x 
  serial: <filter> UEFI [Legacy]: American Megatrends v: 5220 
  date: 09/12/2019 
CPU:
  Topology: 8-Core model: AMD Ryzen 7 1700X bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 1880 MHz min/max: 2200/3400 MHz Core speeds (MHz): 1: 1890 2: 1883 
  3: 1870 4: 1888 5: 1935 6: 1886 7: 1891 8: 1890 9: 1882 10: 1886 11: 1887 
  12: 1888 13: 1887 14: 1887 15: 1888 16: 2065 
Graphics:
  Device-1: NVIDIA GP107 [GeForce GTX 1050 Ti] driver: nvidia v: 440.26 
  Display: x11 server: X.Org 1.20.5 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GTX 1050 Ti/PCIe/SSE2 v: 4.6.0 NVIDIA 440.26 
Audio:
  Device-1: NVIDIA GP107GL High Definition Audio driver: snd_hda_intel 
  Device-2: AMD Family 17h HD Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.3.0-19-generic 
Network:
  Device-1: Intel I211 Gigabit Network driver: igb 
  IF: enp7s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 7.11 TiB used: 2.72 TiB (38.3%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10EZEX-08WN4A0 
  size: 931.51 GiB 
  ID-2: /dev/sdb type: USB vendor: Buffalo model: HD-GDU3 size: 1.82 TiB 
  ID-3: /dev/sdc vendor: Maxtor model: STM3500630AS size: 465.76 GiB 
  ID-4: /dev/sdd type: USB vendor: Western Digital model: WD My Book 25EE 
  size: 2.73 TiB 
  ID-5: /dev/sde vendor: Seagate model: ST3320620AS size: 298.09 GiB 
  ID-6: /dev/sdf vendor: Seagate model: ST1000DX002-2DV162 size: 931.51 GiB 
Partition:
  ID-1: / size: 480.73 GiB used: 14.36 GiB (3.0%) fs: ext4 dev: /dev/sdf1 
  ID-2: /home size: 434.16 GiB used: 101.31 GiB (23.3%) fs: ext4 
  dev: /dev/sdf2 
Sensors:
  System Temperatures: cpu: 43.5 C mobo: 39.0 C gpu: nvidia temp: 55 C 
  Fan Speeds (RPM): cpu: 711 fan-2: 2402 fan-3: 978 fan-5: 0 fan-6: 1305 
  gpu: nvidia fan: 0% 
Info:
  Processes: 414 Uptime: 34m Memory: 31.17 GiB used: 2.36 GiB (7.6%) 
  Shell: bash inxi: 3.0.36 


```

The only thing I can point to is Firefox since that is the only constant thus far.  Like I said it is random.  Sometimes I can go a couple of days something a couple of hours, but only when FF is running.  I have read elsewhere that when caught in an infinite loop, Firefox wont spit out an error, but will freeze the entire system.  When it freezes mouse and keyboard are not responsive, but I am able to do
ALT+ SYSRQ + R E I S U B to restart the system.

I dont know how to troubleshoot a Firefox error and would like some help trying
I have created a new profile also and had same thing happen.

---

### Post by zimbuf on 2019-10-26
There's a kernel-level defect right now with the out of memory routines not being called when the memory levels hit around 90%. The most often times I've hit it are when running Virtualbox with settings that were... a bit too high.

That being said, your issue might not be Firefox, but actually the sites you browse. With modern web frameworks, it's extremely easy to leak memory or file descriptors in the form of unused observable subscriptions, creating too many socket connects due to component re-renders, etc.

Could you attempt to reproduce your normal usage with the same sites and take a snapshot of your current levels of memory so we can rule that out?

---

### Post by scpatl4now on 2019-10-26
I'm not sure I can recreate the exact sites I visit (because I really dont remember them)  but I can say that more times than not I'm watching video on YouTube or another site with video.  What is the best way to monitor memory while I am online that will produce a log?
I actually just had it happen watching a news video clip on the site Mediaite.com.  The audio stuttered about 5 seconds then it crashed (sometimes it reboots...sometimes it just freezes)

---

### Post by zimbuf on 2019-10-26
I was thinking you could just have the system monitor open and watch the RAM utilization. It happening around a video clip would make sense, that's a pretty memory intensive area.

There is a very strong possibility there might be advertisements running cryptominers on the website. Monitor the CPU, as well. Try downloading Ublock Origin and NoScript and selectively allow scripts to run until your videos show up.

But the truth is, is that file I/O has to run through the kernel. If it's from the kernel's OOM manager not running, then the total system deadlock that occurs will also prevent logging.

---

### Post by scpatl4now on 2019-10-27
I used the ** top** command to monitor memory and I saw nothing unsusal for a couple of hours.  Like I said earlier its a very random occurrence, so its hard to pinpoint, but also when I got up this morning the system was frozen with nothing going on.  That has not happened before. I already use Ublock origin.  The thing about logging that has been frustrating is that it stops when things lock so its hard to identify something to report as a bug

---

### Post by Autodave on 2019-10-27
In FF, disable any ad blockers that you have running.  Then, install uBlock (ad blocker).  Give that a shot.

---

### Post by scpatl4now on 2019-10-28
Last night I ran the following in terminal while I was browsing with Firefox

```
sudo top -o +%MEM
```

I noticed that as time went by the buff/cache kept getting larger and larger.  It was not releasing anything back even when I closed tabs.  Even after I closed Firefox it did not return that section back even after a couple of hours idle.  When I started browsing again that number kept increasing and would have used all memory.  The only way to get it to release it was to restart.

[IMG]https://i.imgur.com/gg5ZRvV.png[/IMG]

---

### Post by scpatl4now on 2019-10-28
I use uBlock already.  That is my only ad blocker

---

### Post by twisted_steel on 2019-11-02
Do the random lockups happen while you are away from the computer?  I had an issue with my Ryzen 1700 system where it would randomly lock up.  There was a BIOS change that I solved my issue completely, at least with the AB350 Pro4 motherboard.  It went from random lockups every few days to nothing for over a year.

Advanced > Zen Common Options > Power Supply Idle Control. Change this from Auto to Typical.

Source: [reddit]("https://www.reddit.com/r/Ubuntu/comments/8n55qt/ubuntu_1804_random_freeze/e0h1ssl/")

---


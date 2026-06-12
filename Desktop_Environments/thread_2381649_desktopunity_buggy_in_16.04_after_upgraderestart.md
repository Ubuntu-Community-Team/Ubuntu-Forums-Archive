---
title: "desktop/unity buggy in 16.04 after upgrade/restart"
date: 2018-01-03
forum: Desktop Environments
---

### Post by realityrsv on 2018-01-03
Hi everyone, semi newb here..

Been running ubuntu 16.04 for a few months and just starting to get my head round  few things.  Today was a major brain bender trying (and eventually succeeding) in getting my epson printer to work using CUPS... but i digress...

After this minor success i did a restart (all fine)  then updated the system as i noticed an upgrade waiting in the software centre.  Restarted again and now i have issues, which are:

[LIST]
[*]If i move the mouse over the launcher bar, it dissapears.  about 5-10 seconds later, all the desktop icons disappear too, leaving a nice uncluttered view of my desktop background.  Another 10 seconds or so later, everything reappears again.  If i haven't moved the mouse during this time, i can now click and open a program, otherwise the cycle continues.
[*]I cant shutdown or reboot from the top menu, the option drop down but if i click on something, the above problem occurs.
[*]If i do have open windows, they do not always have the x,minimise,maximise buttons or submenus.
[/LIST]

I have searched for solutions and tried various things:

[LIST]
[*]I have reset compiz config (tweaked a value in here a week or so ago to try speed up a very slow system)
[*]tried pretty much everything in here [https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)
[*]tried updating, reinstalling unity and ubuntu desktop.
[/LIST]

I'm not yet aware how i can generate a report that you might find usefull in helping me, but can follow clear instructions.  terminal works fine and i now know how to restart though that etc.

Can anyone help?  Cheers and sorry for long post

---

### Post by realityrsv on 2018-01-03
oh dear... just tried something i had missed from the link i posted above  (mv ~/.config/dconf/user ~/.config/dconf/user.old)
this has reset the launcher completely (it is back on the left of screen and missing some apps i had added to it) and my background pic has been replaced with the default.  but the problem persist.

I logged in to a guest session to see if that had the same issues (it did) and provoked a crash report.  It was too long to write it all down and i couldn't copy.  the jist of it was:

executable path
/usr/bin/compiz

compiz crashed with SIGSEGV

---

### Post by ventrical on 2018-01-05
Please install..

```

sudo apt-get install inxi

```

then enter into terminal.

```

inxi -Fxz

```

 and report the results here please.

Thank you.

---

### Post by wayne-iba on 2018-01-06
> **ventrical said:**
> Please install..

```

sudo apt-get install inxi

```

then enter into terminal.

```

inxi -Fxz

```

 and report the results here please.

Thank you.

I'm experiencing the same issue as the OP. Incidentally, the very top icon (not sure what it is called but it opens a search box for applications) does NOT work by waiting as the other applications do. FWIW.

Here is the output from inxi -Fxz on my computer:
```

bash$ inxi -Fxz
System:    Host: myhost Kernel: 4.10.0-42-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3) Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Veriton L480G v: P01-A4
           Mobo: Acer model: EG43LMK Bios: Acer v: P01-A4 date: 02/22/2010
CPU:       Quad core Intel Core2 Quad Q8400 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 21280
           clock speeds: max: 2670 MHz 1: 2336 MHz 2: 2003 MHz 3: 2003 MHz 4: 2003 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) Resolution: 1280x1024@60.02hz
           GLX Renderer: Mesa DRI Intel G45/G43 GLX Version: 2.1 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 82801JI (ICH10 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
Network:   Card-1: Ralink RT3090 Wireless 802.11n 1T/1R PCIe driver: rt2800pci v: 2.3.0 bus-ID: 01:00.0
           IF: wlp1s0 state: up mac: <filter>
           Card-2: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: e800 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (32.9% used) ID-1: /dev/sda model: ST3500418AS size: 500.1GB temp: 37C
Partition: ID-1: / size: 55G used: 11G (20%) fs: ext4 dev: /dev/sda7
           ID-2: /home size: 110G used: 51G (49%) fs: ext4 dev: /dev/sda5
           ID-3: swap-1 size: 3.99GB used: 0.08GB (2%) fs: swap dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 30.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 233 Uptime: 5:49 Memory: 2634.9/3915.3MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 
bash$ 

```

---

### Post by interglossa on 2018-01-06
I am so glad people are on this. This has also been reported in askubuntu

[https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-latest-updates-compiz-segfaults/992870](https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-latest-updates-compiz-segfaults/992870)

and if you look at this 

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1741447](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1741447)

and go down to axoin's response, s/he claims that downgrading mesa actually solved the problem.

I hope this is fixed quickly.  I have been using LTS releases for 10 years and this is the worst regression I have seen yet.

---

### Post by iraj1101 on 2018-01-07
I am having exactly the same problem. This is definitely the worst 'regression' I have experienced with Ubuntu as well. Also running 16.04 LTS. ALT + TAB also does not behave properly.

Here is output from inxi -Fxv:

System:    Host: imran-LifeBook-T5010 Kernel: 4.10.0-42-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
Machine:   System: FUJITSU product: LifeBook T5010
           Mobo: FUJITSU model: FJNB1EA
           Bios: FUJITSU // Phoenix v: Version 3.05 date: 08/20/2009
CPU:       Dual core Intel Core2 Duo P8600 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 9576
           clock speeds: max: 2401 MHz 1: 1600 MHz 2: 1600 MHz
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1280x800@59.92hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express
           GLX Version: 2.1 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
Network:   Card-1: Intel 82567LM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 1840 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Intel Ultimate N WiFi Link 5300
           driver: iwlwifi bus-ID: 18:00.0
           IF: wlp24s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (62.1% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: 500.1GB temp: 0C
Partition: ID-1: / size: 451G used: 282G (66%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 8.45GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 60.0C mobo: 26.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 209 Uptime: 2:04 Memory: 6197.7/7850.2MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

---

### Post by carlf39 on 2018-01-07
I am having same problem.  Here is my info... 

carlf39@Inspiron-1110:~$ inxi -Fxz
System:    Host: Inspiron-1110 Kernel: 4.10.0-28-generic i686 (32 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Dell model: 0KC6FD v: A06 Bios: Dell v: A06 date: 12/01/2009
CPU:       Single core Intel Celeron 743 (-UP-) cache: 1024 KB
           flags: (lm nx pae sse sse2 sse3 ssse3) bmips: 2593 speed: 1296 MHz (max)
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.08hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express x86/MMX/SSE2
           GLX Version: 2.1 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-28-generic
Network:   Card-1: Qualcomm Atheros AR8132 Fast Ethernet
           driver: atl1c v: 1.0.1.1-NAPI port: 2000 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-2: Broadcom BCM4312 802.11b/g LP-PHY
           driver: wl bus-ID: 08:00.0
           IF: wlp8s0 state: up mac: <filter>
Drives:    HDD Total Size: 1000.2GB (2.9% used)
           ID-1: /dev/sda model: ST1000LM048 size: 1000.2GB temp: 32C
Partition: ID-1: / size: 189G used: 26G (15%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 2.07GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 187 Uptime: 26 min Memory: 718.6/1942.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

---

### Post by kgord99 on 2018-01-07
Good Day,
Relative Noob to Ubuntu 1604 (loaded on pc in August-September 2017). I am seeing the same issue since January 4-5th, 2018??? There was an update that occurred on the 4th or 5th and I started seeing the disappearing launcher and window frames as described in the original post above.
Sorry, I don't know just what or how to provide some details on my system to help in troubleshooting this. I tried following some remedies in askubuntu after finding a bunch of "half installed/configured" lines in the dpkg.log. No success with those efforts but no further damage either. I did much of what realityrsv wrote in his original post to resolve.
I have about reached the limit of my skill set on this and am hoping a resolution is found that can be dumbed down for my understanding. I did review the entry above (entry by interglossa, in second link, by axoin) that referred to manually downloading mesa/17.0.7-0ubuntu0-16.04.2 and build/13231714. But I am not figuring out the download and install steps(s) (sudo dpkg -i *.deb keep getting errors of file not found?) as outlined in that entry.
I did check my video card performance in Windows 10 (dual boot on this same pc) and noted no issues there. 
Thanks for your time. I do appreciate it!

Gord K

---

### Post by definitelynot73l1p3 on 2018-01-07
I'm in the same problems as you guys, here's what the inxi stuff showme, i hope we can find the answer soon :,v
System:    Host: FELIPE-UBUNTU Kernel: 4.10.0-42-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: HP 430 Notebook PC v: 058D100000204C10002000100
           Mobo: Hewlett-Packard model: 3674 v: 28.4A
           Bios: Hewlett-Packard v: F.38 date: 12/17/2011
CPU:       Dual core Intel Core i3 M 380 (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10108
           clock speeds: max: 2533 MHz 1: 1199 MHz 2: 1599 MHz 3: 1199 MHz
           4: 1333 MHz
Graphics:  Card: Intel Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.10hz
           GLX Renderer: Mesa DRI Intel Ironlake Mobile
           GLX Version: 2.1 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 5 Series/3400 Series High Definition Audio
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 01:00.0
           IF: eno1 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k bus-ID: 02:00.0
           IF: wlo1 state: up mac: <filter>
Drives:    HDD Total Size: 250.1GB (9.9% used)
           ID-1: /dev/sda model: WDC_WD2500BEVT size: 250.1GB temp: 48C
           ID-2: /dev/mmcblk0 model: N/A size: 31.1GB
Partition: ID-1: / size: 73G used: 23G (33%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 1.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 57.0C mobo: 52.0C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 245 Uptime: 50 min Memory: 3300.5/5763.4MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

---

### Post by kgord99 on 2018-01-07
Good Day once again...
I followed this link, [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1741447](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1741447), found in interglossa's entry above and followed the suggestions by axoin.
I stumbled upon the fixes to my errors in downloading and installing those files and rebooted.
I had to make some further changes with Package Manager but things are much improved. EDIT...I had to perform the install and Package Manager routines with the other user on this Ubuntu box to have everything back on track. As it looks like now.
Thank you for the info!
I look forward to the day when I can help a fellow noob. I will endeavor to NOT be a pest until such time.
Take care.

Gord K

---

### Post by monkeybrain20122 on 2018-01-08
Wow that is pretty bad. Mesa update should not be mandatory unless it is a security issue. I guess I lucked out for skipping 17.2.4 and directly onto mesa 17.3.1
 ```
glxinfo | grep OpenGLOpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL core profile version string: 4.2 (Core Profile) Mesa 17.3.1 - padoka PPA
OpenGL core profile shading language version string: 4.20
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.3.1 - padoka PPA
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 17.3.1 - padoka PPA
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
```

You can update all mesa packages to 17.3.1 with this [ppa]("https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/pkppa"), and then disable it if everything is working so it won't get further updates in case it may mess up your system again, personally I test the upgrade in a test installation in an external drive before I go ahead in the real system.

---

### Post by mc4man on 2018-01-08
Seems to be more vendor than Intel specific. Here I've a 3rd gen (ivybridge) and 4th gen (haswell), both Lenovo. Neither are affected by the mesa update at all. 
For those affected the 17.3.1 version should be good.. (currently ppa but it or commits from will show up in 16.04 repos in due course

---

### Post by kgord99 on 2018-01-08
Thanks for all the responses to this issue.
I was happy to see a great improvement in my pc's performance after downloading the files as suggested by axoin but...I was still seeing some dependency errors. In trying to correct those, I miscued in a major way and ended up having to do a reinstall of 1604 LTS. No fault related to the original issue. Noob digging into things unfamiliar and failing to read and heed dialog boxes! Never heard of that before LOL.
Anyway the entry from monkeybrain20122 with the ppa to 17.3.1 got me past the dependency errors and I think I am on my way to smooth sailing-just like what I have been enjoying since September!
Thanks again for all your suggestions. It helped this Noob immensley.
Take care.

Gord K

---

### Post by wayne-iba on 2018-01-13
Just to clarify, I do not think the issue at the link kgord99 includes is what we are experiencing here. At least speaking for myself, my issue is not with the window manager or gui, but with the launcher and alt-tab switcher.

---

### Post by wayne-iba on 2018-01-15
Out of curiosity: does anyone who has experienced this problem also have a 16.04.3 system that does *not* exhibit the problem? I'm wondering as the 16.04.3 system I have is rather old hardware. I'm not willing to upgrade my other two systems from 16.04.2 just to find out, but it might help folks who are trying to fix this if we can narrow down the situations where this manifests.

---

### Post by wayne-iba on 2018-01-16
I have resolved this on my machine. (And incidentally, the problem was specific to older hardware after all.)

See this thread for instructions on getting the patch: [https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-updates-2018-01-04-compiz-segfaults](https://askubuntu.com/questions/992571/gui-unity-crashing-in-16-04-lts-after-updates-2018-01-04-compiz-segfaults)

---


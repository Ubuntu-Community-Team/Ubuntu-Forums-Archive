---
title: "Serious performance problem - please help!"
date: 2005-11-16
forum: Gaming &amp; Leisure
---

### Post by plcdfa on 2005-11-16
Ok, I post it here cos I'm not at all convinced that my problem is hardware or driver related. Altough if the moderators find it inappropriate, please just move it to hardware or where you see fit.

The problem is that my 3D performance is extremely bad in Breezy as opposed to Hoary. My hardware's by no means new and shiny, but consider this one: Neverwinter Nights under Hoary ran with an accaptable 40 fps, now it's suffering with 6-8(!) no matter what I try. Also I can't play ET with all the options set to minimum, while in windows it runs smoothly with almost everything set to max.
I tried tweaking the games video settings, and giving them higher (...I mean lower:) ) priorities, but that didn't help. (Not even easing the problem to a considerable degree, which is quite strange... :confused: ) I think they might be conflicting with something, but I've run out of ideas.

Here's my specs:
Kubuntu 5.10 (clean install) with the 686 kernel from the repos
Celeron 1 GHz
256 MB RAM
Inno3D Geforce FX 5200 (128 MB RAM) AGP 4x with the 7174 driver from the nvidia website (I couldn't install the newer ones, cos they freeze the system at X startup.:confused: Don't think this causes the problem though, this isn't an old driver either, it dates 2005.03.31.)

Here are the interesting parts from my xorg.conf:
```
Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```
```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
```
Please just ask if I forgot something...
And this is the output of ps aux: (that's the command to list all running processes, isn't it? I'm a linux newbie.:oops: )
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   1560   528 ?        S    16:16   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   16:16   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   16:16   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   16:16   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   16:16   0:00 [kthread]
root         7  0.0  0.0      0     0 ?        S<   16:16   0:00 [kacpid]
root        82  0.0  0.0      0     0 ?        S<   16:16   0:00 [kblockd/0]
root       106  0.0  0.0      0     0 ?        S    16:16   0:00 [pdflush]
root       107  0.0  0.0      0     0 ?        S    16:16   0:00 [pdflush]
root       109  0.0  0.0      0     0 ?        S<   16:16   0:00 [aio/0]
root       108  0.0  0.0      0     0 ?        S    16:16   0:00 [kswapd0]
root       694  0.0  0.0      0     0 ?        S    16:16   0:00 [kseriod]
root      2334  0.0  0.0      0     0 ?        S    16:16   0:00 [khubd]
root      3905  0.0  0.0      0     0 ?        S    16:16   0:00 [kjournald]
root      4063  0.0  0.2   1660   564 ?        S<s  16:16   0:00 udevd --daemon
root      6818  0.0  0.0      0     0 ?        S    16:16   0:00 [kgameportd]
dhcp      7017  0.0  0.4   2328  1120 ?        Ss   16:17   0:00 dhclient3 -pf /
root      7369  0.0  0.3   1820  1020 ?        Ss   16:17   0:00 /usr/sbin/acpid
syslog    7384  0.0  0.2   1764   756 ?        Ss   16:17   0:00 /sbin/syslogd -
root      7401  0.0  0.1   1564   400 ?        Ss   16:17   0:00 /bin/dd bs 1 if
klog      7403  0.0  0.6   2564  1540 ?        Ss   16:17   0:00 /sbin/klogd -P
105       7416  0.0  0.4   2140  1040 ?        Ss   16:17   0:00 /usr/bin/dbus-d
hal       7429  0.0  1.4   5056  3800 ?        Ss   16:17   0:00 /usr/sbin/hald
hal       7434  0.0  0.2   1864   592 ?        S    16:17   0:00 hald-addon-acpi
hal       7443  0.0  0.2   1864   632 ?        S    16:17   0:00 hald-addon-stor
hal       7445  0.0  0.2   1864   632 ?        S    16:17   0:00 hald-addon-stor
cupsys    7466  0.0  1.2   6300  3296 ?        Ss   16:17   0:00 /usr/sbin/cupsd
hplip     7488  0.0  0.4  12612  1280 ?        Ssl  16:17   0:00 /usr/sbin/hpiod
hplip     7498  0.0  2.2   8844  5852 ?        S    16:17   0:00 python /usr/sbi
root      7936  0.0  0.3   2788   952 ?        S    16:17   0:00 /usr/bin/xfstt
root      7941  0.0  0.2   2584   740 ?        Ss   16:17   0:00 /usr/bin/kdm
nobody    7944  0.0  0.4   2260  1036 ?        Ss   16:17   0:01 ksysguardd -d
root      7955  4.5  9.1  27352 23476 ?        SL   16:17   1:44 /usr/X11R6/bin/
root      7957  0.0  0.5   3192  1348 ?        S    16:17   0:00 -:0
daemon    7981  0.0  0.2   1752   656 ?        Ss   16:17   0:00 /usr/sbin/atd
root      8002  0.0  0.3   1812   852 ?        Ss   16:17   0:00 /usr/sbin/cron
root      8022  0.0  0.1   1556   492 tty1     Ss+  16:17   0:00 /sbin/getty 384
root      8023  0.0  0.1   1556   492 tty2     Ss+  16:17   0:00 /sbin/getty 384
beci      8040  0.0  0.6   5056  1608 ?        Ss   16:20   0:00 /bin/sh /usr/bi
beci      8074  0.0  0.3   3120  1004 ?        Ss   16:20   0:00 /usr/bin/ssh-ag
beci      8098  0.0  4.2  25944 10936 ?        Ss   16:20   0:00 kdeinit Running
beci      8101  0.0  3.7  24764  9616 ?        S    16:20   0:00 dcopserver [kde
beci      8103  0.0  4.4  27032 11400 ?        S    16:20   0:00 klauncher [kdei
beci      8106  0.1  6.3  30448 16224 ?        S    16:20   0:02 kded [kdeinit]
beci      8108  0.0  0.5   2704  1452 ?        S    16:20   0:00 /usr/lib/gamin/
beci      8112  0.3  3.7  48060  9724 ?        S    16:20   0:07 artsd -F 10 -S
beci      8123  0.0  5.1  27508 13328 ?        S    16:20   0:00 kaccess [kdeini
beci      8124  0.0  0.7   4268  1912 ?        S    16:20   0:00 /usr/bin/ivman
beci      8125  0.0  0.1   1544   340 ?        S    16:20   0:00 kwrapper ksmser
beci      8130  0.0  5.2  27688 13536 ?        S    16:20   0:00 ksmserver [kdei
beci      8131  0.1  6.1  29740 15816 ?        S    16:20   0:02 kwin [kdeinit]
beci      8137  0.1  6.9  30920 17796 ?        S    16:20   0:02 kdesktop [kdein
beci      8144  0.5  9.4  38728 24256 ?        S    16:20   0:12 kicker [kdeinit
beci      8145  0.0  4.7  27904 12128 ?        S    16:20   0:00 kio_file [kdein
beci      8148  0.0  5.6  27960 14612 ?        S    16:20   0:01 kbluetoothd --d
beci      8151  0.1  8.9  37816 22868 ?        S    16:20   0:02 konqueror [kdei
beci      8152  0.5  6.8  31796 17692 ?        R    16:20   0:10 konsole [kdeini
beci      8153  0.0  6.2  29424 16064 ?        S    16:20   0:01 katapult -sessi
beci      8154  4.2 11.1  53608 28676 ?        S    16:20   1:28 /usr/lib/opera/
beci      8155  0.0  0.8   5416  2056 pts/1    Ss+  16:21   0:00 /bin/bash
beci      8156  0.0  0.8   5416  2064 pts/2    Ss   16:21   0:00 /bin/bash
beci      8165  0.0  7.9  36532 20380 ?        S    16:21   0:01 konqueror [kdei
beci      8167  0.0  7.7  37904 19896 ?        S    16:21   0:01 knotify [kdeini
beci      8168  0.0  7.9  36532 20396 ?        S    16:21   0:01 konqueror [kdei
beci      8184  0.0  6.3  30368 16412 ?        S    16:21   0:00 kio_uiserver [k
beci      8225  0.0  1.7   8484  4544 ?        S    16:41   0:00 /usr/lib/opera/
beci      8226  0.0  0.1   1568   340 ?        S    16:41   0:00 /usr/lib/opera/
beci      8261  8.9  7.6  30680 19536 ?        Ss   16:49   0:32 ksysguard --sho
beci      8262  1.5  0.4   2252  1028 ?        S    16:49   0:05 ksysguardd
beci      8263  0.0  4.6  26632 11852 ?        S    16:49   0:00 kio_file [kdein
beci      8264  2.5 10.5  43656 26952 ?        S    16:50   0:07 krusader -capti
beci      8265  0.0  4.6  26632 11844 ?        S    16:50   0:00 kio_file [kdein
beci      8280  0.0  0.4   4592  1040 pts/2    R+   16:55   0:00 ps aux

```
If you've got the smallest idea on which I could start looking for a solution, please share it. I like Linux very much otherwise, Ubuntu beats the sh*t out of Win, but I wanna believe it's also a  better gaming platform.  :D 
Thanks in advence!
Oh, and sorry for the possible grammar mistakes, I'm not a native english speaker.

---

### Post by plcdfa on 2005-11-22
Oh, come on, please! Don't you have an idea what to check here? If I'm posting it the wrong place, just redirect me where I could get help.:(

---

### Post by 23meg on 2005-11-22
Please paste the output of the command ```
glxinfo |grep direct
```

---

### Post by plcdfa on 2005-11-28
Ok, sorry for the late reply, the output is:
direct rendering: No

Could this be the problem, and how can I enable it?

---

### Post by plcdfa on 2005-12-02
OK, problem solved by installing the latest nvidia drivers. Thanks for the not-so-enthusiast help. Just kidding.;-) It's quite strange afterall, cos this same driver used to freeze X when I tried it a month ago. :confused: Installing the driver pack from the nvidia site seems to be a pain in Breezy, which is odd as I succeded instantly with it under Hoary. (As a complete Linux newbie :cool: ) 
This time I had to experience with different versions, and the one which turned out to work at last also refused to load the kernel module automatically at startup, so I had to add it to /etc/modules. Maybe I messed up things with all this (though I tried to clean up after every install attempt), as I couldn't reenable direct rendering with the old driver, no matter what I tried. Anyway, if someone happens to have an explanation for all this weird behaviour, please post it. I really am curious. Just learning Linux you know.:)

---

### Post by Kadin2048 on 2005-12-19
Just wondering, which version of the drivers did you end up installing? And did you use the actual install script that you download from the NVidia site? Or do it some other way?

I ask because I tried getting the latest ones from NVidia but never got it to work (it kept complaining about runlevels) and before I found a solution to that I had gone and installed the ones from the repository. Now I wonder if I inadvertently got an old version.

Anyway just curious; it seems that some people have wildly different luck with different versions of the drivers...

---

### Post by frodon on 2005-12-19
**plcdfa**, why don't you have this option in the device section ? : ```
Option          "RenderAccel"           "true"
```It could be the problem.

---


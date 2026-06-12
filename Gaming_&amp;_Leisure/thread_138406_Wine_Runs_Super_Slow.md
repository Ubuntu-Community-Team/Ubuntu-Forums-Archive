---
title: "Wine Runs Super Slow"
date: 2006-03-01
forum: Gaming &amp; Leisure
---

### Post by squirrelplayingtag on 2006-03-01
I'm running Ubuntu 5.10 and I did manage to get wine installed without an issue and did get steam installed but wine runs sooo slow. I type "winecfg" and it takes about 5 mins for the configuration window to appear. Also starting steam with wine ~/.wine/drive_c/Program\ Files/Steam/Steam.exe takes about 5-7 minutes to start. Once steam loads it respondes extremely slow. I have not even been able to get into Counter Strike because it is so slow. To stop it from running I have to do ctrl + alt + backspace and log back in.

Output of top for me and root:
```

top - 22:04:51 up 3 days,  6:04,  2 users,  load average: 13.66, 9.31, 5.20
Tasks:  84 total,   5 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s): 43.2% us, 56.4% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:    515796k total,   505352k used,    10444k free,    64012k buffers
Swap:  1461872k total,    14840k used,  1447032k free,   139496k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
17403 dave      15   0 1905m  67m  25m R 35.3 13.5  23:31.76 wine-preloader
17406 dave      15   0  3884 1792  816 S 30.7  0.3  18:49.64 wineserver
17717 dave      15   0 39008  14m 8992 S  6.6  2.8   0:03.64 gnome-terminal
12273 dave      15   0 30060  16m  10m S  3.0  3.3  10:30.88 gaim
 8344 dave      16   0 17944  10m 6252 S  1.3  2.1   3:30.99 xfdesktop
17745 dave      16   0  2128 1088  844 R  0.7  0.2   0:00.09 top
 7329 dave      16   0  3076 1548 1196 S  0.0  0.3   0:00.02 esd
 7376 dave      15   0  2700 1440  888 S  0.0  0.3   0:09.23 gam_server
 8278 dave      19   0  4308 1572 1012 S  0.0  0.3   0:00.08 sh
 8317 dave      16   0  3124 1004  808 S  0.0  0.2   0:00.04 ssh-agent
 8320 dave      25   0  2032  740  644 S  0.0  0.1   0:00.00 dbus-daemon
 8321 dave      15   0  2572  748  624 S  0.0  0.1   0:00.00 dbus-launch
 8325 dave      24   0  4308 1560 1000 S  0.0  0.3   0:00.00 sh
 8326 dave      15   0  7092 3688 2600 S  0.0  0.7   0:07.11 xscreensaver
 8330 dave      16   0 12140 5088 4068 S  0.0  1.0   0:25.42 xfce4-session
 8335 dave      15   0 17540 9768 6576 S  0.0  1.9   0:23.06 xfce-mcs-manage
 8338 dave      15   0 13112 6988 5392 S  0.0  1.4   0:33.93 xfwm4
 8340 dave      16   0 13456 7708 5392 S  0.0  1.5   2:00.20 xftaskbar4
 8342 dave      16   0 13468 7716 5400 S  0.0  1.5   2:01.01 xftaskbar4
 8346 dave      15   0 18640  11m 6808 S  0.0  2.3   7:11.68 xfce4-panel
 8353 dave      16   0 27676  12m  10m S  0.0  2.5   0:01.48 konqueror
 8364 dave      16   0 24716  10m 8700 S  0.0  2.1   0:00.55 kdeinit
 8367 dave      15   0 23900 9564 8380 S  0.0  1.9   0:00.21 dcopserver
 8369 dave      16   0 24812  10m 9432 S  0.0  2.1   0:00.17 klauncher
 8371 dave      16   0 28352  15m  12m S  0.0  3.1   0:03.06 kded
 8864 dave      15   0 34600  17m  13m S  0.0  3.5   0:15.10 knotify
 8885 dave      15   0 12824 7712 5080 S  0.0  1.5   0:02.52 artsd
15167 dave      16   0 12336 6756 5156 S  0.0  1.3   0:05.00 xftaskbar4
16502 dave      22   0  4332 1640 1056 S  0.0  0.3   0:00.02 firefox
16513 dave      24   0  4372 1668 1040 S  0.0  0.3   0:00.02 run-mozilla.sh
16518 dave      16   0  118m  54m  17m S  0.0 10.8   9:16.66 firefox-bin
16522 dave      16   0  6360 3632 1692 S  0.0  0.7   0:00.45 gconfd-2
17386 dave      16   0  8612 3400 2220 S  0.0  0.7   0:00.30 xterm
17387 dave      16   0  4624 2036 1320 S  0.0  0.4   0:00.03 bash
17400 dave      16   0 25748  11m 9576 S  0.0  2.2   0:00.02 kio_file
17721 dave      18   0  6356 2712 2132 S  0.0  0.5   0:00.20 bonobo-activati
17722 dave      16   0  2268  708  584 S  0.0  0.1   0:00.00 gnome-pty-helpe
17723 dave      16   0  4624 2008 1292 S  0.0  0.4   0:00.02 bash
17744 dave      18   0 11224 4404 3512 R  0.0  0.9   0:00.10 mousepad

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8255 root      15   0  206m 112m  12m S  5.6 22.3 293:55.12 Xorg
    1 root      16   0  1564  532  460 S  0.0  0.1   0:02.24 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:01.61 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.03 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   75 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
  103 root      15   0     0    0    0 S  0.0  0.0   0:10.01 pdflush
  104 root      15   0     0    0    0 S  0.0  0.0   0:00.30 pdflush
  106 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  105 root      15   0     0    0    0 S  0.0  0.0   0:01.10 kswapd0
  691 root      15   0     0    0    0 S  0.0  0.0   0:00.01 kseriod
 1831 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2884 root      10  -5     0    0    0 S  0.0  0.0   0:00.17 reiserfs/0
 3010 root      15  -4  1656  564  484 S  0.0  0.1   0:00.29 udevd
 6277 root      16   0  1560  396  328 S  0.0  0.1   0:00.10 dd
 6717 root      16   0 10608 2580 2060 S  0.0  0.5   0:00.00 gdm
 7018 root      16   0  5596 2012 1472 S  0.0  0.4   0:01.76 nmbd
 7020 root      17   0  7720 2664 2032 S  0.0  0.5   0:00.00 smbd
 7043 root      18   0  3540 1528 1280 S  0.0  0.3   0:00.00 sshd
 7068 root      18   0  7720 2648 2016 S  0.0  0.5   0:00.00 smbd
 7077 root      18   0  1920  812  712 S  0.0  0.2   0:00.00 hcid
 7083 root      18   0  1604  548  480 S  0.0  0.1   0:00.00 sdpd
 7093 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 7138 root      16   0  1936  852  716 S  0.0  0.2   0:00.03 cron
 7180 root      16   0  1556  492  424 S  0.0  0.1   0:00.00 getty
 7181 root      16   0  1556  492  424 S  0.0  0.1   0:00.00 getty
 7182 root      16   0  1556  488  424 S  0.0  0.1   0:00.00 getty
 7183 root      16   0  1556  492  424 S  0.0  0.1   0:00.00 getty
 8250 root      15   0 10936 3044 2468 S  0.0  0.6   0:00.03 gdm
10196 root      26  10  1956 1024  556 S  0.0  0.2   0:00.01 acpid
12286 root      17   0  1556  492  424 S  0.0  0.1   0:00.01 getty
12299 root      17   0  1556  488  424 S  0.0  0.1   0:00.02 getty

```

---

### Post by Zeroangel on 2006-03-01
I'm having similar problems with a game called 'Battlezone II'. The official WINE likes to take up huge amounts of memory (1.5gb) even though the game is designed to utilize 256MB of RAM. And the game runs at 10fps with all graphical features disabled (it would run at +60fps in Windows, but 10fps seems far too low even for WINE).

I've managed to improve the situation by turning on some options in /etc/X11/xorg.conf:```
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
[b]        Option          "NoLogo"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"[/b]
EndSection
```But the speed improvements aren't exactly mind-blowing. And RenderAccel tends to undermine system stability.

I would appreciate it if someone here could post additional tweaks. :D

---

### Post by nouse66 on 2006-04-01
Did you ever find out what was causing the 5 minute delay on startup?  I'm having the same issue when I run winecfg.  Some windows programs get the delay (dvdshrink) and others don't (windows media player).

---

### Post by squirrelplayingtag on 2006-04-01
Nope. When ever I want to play counter strike I go use the family computer.

---

### Post by nouse66 on 2006-04-04
ok, i figured out what was causing it for me.  for some reason my loopback interface (lo) didn't get set to start on boot so 127.0.0.1 wasn't available.  the installer didn't even set up eth0 correctly but i fixed right away since it's more noticable.   i never bothered to look at the loopback... figured that would be somewhat idiot-proof in the installer. 
someone tell me that the dapper version of the installer is less buggy ](*,) 

i don't really think that it would be why counterstrike is slow but it's definitly a network issue that causes wine to hang for a few minutes.  more info here:
[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/ef7e4a132bbdb888/c5faab58debd7993?q=startup&rnum=1#c5faab58debd7993]("http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/ef7e4a132bbdb888/c5faab58debd7993?q=startup&rnum=1#c5faab58debd7993")

---


---
title: "Broke Desktop and compiz is now slow"
date: 2009-05-05
forum: General Help
---

### Post by LowSky on 2009-05-05
So i ran the screensaver as wallpaper hack, and now I have broken my desktop after turning it off

I used these commands to get the screensaver to be the wallpaper
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```
```
/usr/lib/xscreensaver/glmatrix -root
```

then turned it off with this

```
gconftool-2 –type bool –set /apps/nautilus/preferences/show_desktop true && nautilus
```

Now I cant right click on the desktop to bring up options and compiz is running slow like molasses 

Any idea how to fix? I already checked gconf-editor and the show volumes is already checked


I'm feeling like an idiot

should I just run

```
cd /home/john rm -rf .gnome2 .gconf .gconfd .metacity 
```

then reboot?

---

### Post by GrouchoMarx on 2009-05-05
Is glmatrix still running? You could try "killall glmatrix".

---

### Post by JK3mp on 2009-05-05
run ps -A and see what proccesses or going. OR try disabling or shutting off compiz effects and see if any recovery there..

---

### Post by LowSky on 2009-05-05
ok turned off compiz and restarted no change....

```
john@john-desktop:~$ sudo killall -9 glmatrix
glmatrix: no process killed

```

```
john@john-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:00 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:00 events/0
   16 ?        00:00:00 events/1
   17 ?        00:00:00 events/2
   18 ?        00:00:00 events/3
   19 ?        00:00:00 khelper
   20 ?        00:00:00 kstop/0
   21 ?        00:00:00 kstop/1
   22 ?        00:00:00 kstop/2
   23 ?        00:00:00 kstop/3
   24 ?        00:00:00 kintegrityd/0
   25 ?        00:00:00 kintegrityd/1
   26 ?        00:00:00 kintegrityd/2
   27 ?        00:00:00 kintegrityd/3
   28 ?        00:00:00 kblockd/0
   29 ?        00:00:00 kblockd/1
   30 ?        00:00:00 kblockd/2
   31 ?        00:00:00 kblockd/3
   32 ?        00:00:00 kacpid
   33 ?        00:00:00 kacpi_notify
   34 ?        00:00:00 cqueue
   35 ?        00:00:00 ata/0
   36 ?        00:00:00 ata/1
   37 ?        00:00:00 ata/2
   38 ?        00:00:00 ata/3
   39 ?        00:00:00 ata_aux
   40 ?        00:00:00 ksuspend_usbd
   41 ?        00:00:00 khubd
   42 ?        00:00:00 kseriod
   43 ?        00:00:00 kmmcd
   44 ?        00:00:00 btaddconn
   45 ?        00:00:00 btdelconn
   46 ?        00:00:00 pdflush
   47 ?        00:00:00 pdflush
   48 ?        00:00:00 kswapd0
   49 ?        00:00:00 aio/0
   50 ?        00:00:00 aio/1
   51 ?        00:00:00 aio/2
   52 ?        00:00:00 aio/3
   53 ?        00:00:00 ecryptfs-kthrea
   56 ?        00:00:00 scsi_eh_0
   57 ?        00:00:00 scsi_eh_1
   58 ?        00:00:00 scsi_eh_2
   59 ?        00:00:00 scsi_eh_3
   60 ?        00:00:00 scsi_eh_4
   61 ?        00:00:00 scsi_eh_5
   62 ?        00:00:00 kstriped
   63 ?        00:00:00 kmpathd/0
   64 ?        00:00:00 kmpathd/1
   65 ?        00:00:00 kmpathd/2
   66 ?        00:00:00 kmpathd/3
   67 ?        00:00:00 kmpath_handlerd
   68 ?        00:00:00 ksnapd
   69 ?        00:00:00 kondemand/0
   70 ?        00:00:00 kondemand/1
   71 ?        00:00:00 kondemand/2
   72 ?        00:00:00 kondemand/3
   73 ?        00:00:00 krfcommd
  405 ?        00:00:00 khpsbpkt
  658 ?        00:00:00 knodemgrd_0
  831 ?        00:00:00 kjournald2
  965 ?        00:00:00 udevd
 1714 ?        00:00:00 kpsmoused
 2139 ?        00:00:00 kjournald2
 2143 ?        00:00:00 mount.ntfs-3g
 2147 ?        00:00:00 mount.ntfs-3g
 2433 tty4     00:00:00 getty
 2434 tty5     00:00:00 getty
 2437 tty2     00:00:00 getty
 2439 tty3     00:00:00 getty
 2441 tty6     00:00:00 getty
 2515 ?        00:00:00 acpid
 2554 ?        00:00:00 syslogd
 2577 ?        00:00:00 dd
 2579 ?        00:00:00 klogd
 2602 ?        00:00:00 dbus-daemon
 2771 ?        00:00:00 hddtemp
 2792 ?        00:00:00 chipcardd4
 2811 ?        00:00:00 winbindd
 2833 ?        00:00:00 hald
 2836 ?        00:00:00 winbindd
 2837 ?        00:00:00 console-kit-dae
 2900 ?        00:00:00 hald-runner
 2929 ?        00:00:00 hald-addon-inpu
 2973 ?        00:00:00 hald-addon-stor
 2974 ?        00:00:00 hald-addon-cpuf
 2975 ?        00:00:00 hald-addon-acpi
 2993 ?        00:00:00 bluetoothd
 3026 ?        00:00:00 gdm
 3027 ?        00:00:00 gdm
 3033 tty7     00:02:15 Xorg
 3053 ?        00:00:00 NetworkManager
 3072 ?        00:00:00 avahi-daemon
 3073 ?        00:00:00 avahi-daemon
 3076 ?        00:00:00 wpa_supplicant
 3078 ?        00:00:00 nm-system-setti
 3101 ?        00:00:00 cupsd
 3128 ?        00:00:00 system-tools-ba
 3201 ?        00:00:00 atd
 3229 ?        00:00:00 cron
 3339 ?        00:00:17 chipcardd4
 3340 tty1     00:00:00 getty
 3355 ?        00:00:00 dhclient
 3420 ?        00:00:00 gnome-keyring-d
 3433 ?        00:00:00 x-session-manag
 3491 ?        00:00:00 ssh-agent
 3494 ?        00:00:00 dbus-launch
 3495 ?        00:00:00 dbus-daemon
 3500 ?        00:00:00 pulseaudio
 3501 ?        00:00:00 gconf-helper
 3503 ?        00:00:01 gconfd-2
 3514 ?        00:00:00 seahorse-agent
 3517 ?        00:00:00 gvfsd
 3523 ?        00:00:00 gvfs-fuse-daemo
 3532 ?        00:00:01 gnome-settings-
 3540 ?        00:00:10 gnome-panel
 3543 ?        00:00:00 bonobo-activati
 3545 ?        00:00:00 fusion-icon
 3547 ?        00:00:00 python
 3550 ?        00:00:00 evolution-alarm
 3551 ?        00:00:00 nm-applet
 3556 ?        00:00:00 update-notifier
 3558 ?        00:00:00 bluetooth-apple
 3562 ?        00:00:00 notify-osd
 3564 ?        00:00:00 gnome-power-man
 3576 ?        00:00:00 trashapplet
 3580 ?        00:00:00 gvfsd-trash
 3602 ?        00:00:00 gvfs-hal-volume
 3610 ?        00:00:00 gvfs-gphoto2-vo
 3618 ?        00:00:20 multiload-apple
 3622 ?        00:00:00 drivemount_appl
 3624 ?        00:00:00 mixer_applet2
 3626 ?        00:00:00 indicator-apple
 3646 ?        00:00:02 gnome-screensav
 3651 ?        00:00:00 evolution-data-
 3655 ?        00:00:00 evolution-excha
 3987 ?        00:00:00 gvfsd-burn
 4096 ?        00:00:24 compiz.real
 4097 ?        00:00:00 sh
 4098 ?        00:00:00 gtk-window-deco
 4100 ?        00:00:47 firefox
 4289 ?        00:03:36 npviewer.bin
 4571 ?        00:00:00 gnome-terminal
 4572 ?        00:00:00 gnome-pty-helpe
 4573 pts/0    00:00:00 bash
 4594 pts/0    00:00:00 ps

```

---

### Post by JK3mp on 2009-05-05
Does everything run fine with compiz off?

---

### Post by GrouchoMarx on 2009-05-05
I just don't see how those two commands would screw up your desktop. Certainly you shouldn't have to delete all those gnome settings. Is it possible that something else is hogging your CPU? npviewer looks like it's taking a lot of time.

---

### Post by LowSky on 2009-05-05
With compiz off I still am not getting desktop files and partitions to show up... getting weird

heres top... i think im going to cleanse my /home folder files if I cant get this to work```
john@john-desktop:~$ top

top - 23:24:57 up  1:14,  2 users,  load average: 0.16, 0.52, 0.60
Tasks: 159 total,   1 running, 158 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.2%sy,  0.0%ni, 99.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3992976k total,  1408456k used,  2584520k free,   389888k buffers
Swap:  9277496k total,        0k used,  9277496k free,   534140k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3339 chipcard  20   0 27584 1796 1096 S    1  0.0   0:29.04 chipcardd4         
 3033 root      20   0  164m  43m  17m S    1  1.1   5:08.97 Xorg               
 3618 john      20   0  214m  12m 9428 S    1  0.3   0:32.97 multiload-apple    
 3540 john      20   0  411m  32m  15m S    0  0.8   0:22.11 gnome-panel        
 5403 john      20   0 19116 1352  988 R    0  0.0   0:00.19 top                
    1 root      20   0  5244 2032  628 S    0  0.1   0:00.86 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
john@john-desktop:~$ 
john@john-desktop:~$ 

```

---

### Post by LowSky on 2009-05-05
ok running this did nothing```
cd /home/john rm -rf .gnome2 .gconf .gconfd .metacity
```

compiz seems to be runnign smooth now. Right click on the desktop still doesn't work, and the files and partitions are still not showing up

I think using a LiveCD to copy some files over, might be a good idea, but what am I missing?

---

### Post by GrouchoMarx on 2009-05-05
I take it you tried restarting nautilus (first "nautilus -q", then "nautilus")? And also restarting the computer?

---

### Post by LowSky on 2009-05-06
yeah, I did. Something changed and I don't know exactly what. 
I hate to say it but I did a reinstall, I know it is not the way I should try to diagnose and fix things, but a 1/2 hour reinstall is better than taking 12 hours to find a solution. And because I dont store personal files in my home folder it makes reinstalls much easier.

thanks for the help guys.

---


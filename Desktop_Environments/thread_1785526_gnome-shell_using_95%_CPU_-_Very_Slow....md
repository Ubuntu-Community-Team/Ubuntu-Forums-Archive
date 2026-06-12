---
title: "gnome-shell using 95% CPU - Very Slow..."
date: 2011-06-18
forum: Desktop Environments
---

### Post by CodyLoco on 2011-06-18
Hi guys,

gnome-shell seems to go into loco mode sometimes on my computer... among other problems I'm having this one is the worst.  So far, it *seems* to happen after a flash movie is loaded in firefox, although I can't tell for sure if that's the case...  Flash performance for some reason is crap anyways on here, I don't know if maybe I need a different version of flash?  Anyways, if you guys have any clues as to wth is going on, that would be awesome! :)  I'm a bit of a newbie so treat me nicely :P

Just a quick update - reloading with r seems to fix the CPU usage issue... until it happens again...

```
top - 08:05:19 up 23:20,  2 users,  load average: 1.31, 0.74, 0.37
Tasks: 203 total,   3 running, 198 sleeping,   0 stopped,   2 zombie
Cpu(s): 16.4%us,  2.5%sy,  0.0%ni, 73.4%id,  7.6%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   8118488k total,  6523664k used,  1594824k free,   670112k buffers
Swap:  8309756k total,      168k used,  8309588k free,  3285224k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2040 codyloco  20   0 1092m 331m  44m R   95  4.2 162:05.65 gnome-shell        
12691 root      20   0 52180  36m  760 D   18  0.5   0:24.54 mount.ntfs         
12235 codyloco  20   0  638m  44m  16m S   17  0.6   0:45.49 nautilus           
 1857 root      20   0  172m  50m  16m S    9  0.6  47:35.69 Xorg               
 7000 root      20   0 21952 7512  756 S    6  0.1   0:09.97 mount.ntfs         
 2364 codyloco  20   0 1431m 420m  34m S    4  5.3  87:36.96 firefox-bin        
12872 codyloco  20   0  332m  17m  10m S    2  0.2   0:00.86 gnome-terminal     
 2417 codyloco  20   0  295m  86m  14m S    1  1.1 457:55.61 npviewer.bin       
 3313 codyloco  20   0  290m  69m  15m S    1  0.9  11:36.13 skype              
 1707 codyloco   9 -11  353m  12m 9976 S    0  0.2   6:34.98 pulseaudio         
11732 root      20   0     0    0    0 S    0  0.0   0:02.92 kworker/0:1        
    1 root      20   0 24004 2168 1328 S    0  0.0   0:02.44 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.07 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:04.64 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:01.06 ksoftirqd/1  
```

---

### Post by CodyLoco on 2011-06-19
Bump?

---

### Post by bmbaker on 2011-06-20
i would suggest updating flash first and see if that helps :-)
```
sudo apt-get install gsfonts gsfonts-x11 flashplugin-nonfree
```

also which ppa's are you using?
and which kernel?

---

### Post by _0R10N on 2011-06-20
Wow! I had the same issue with gnome shell. Every once in a while they took over my CPU and that was the primary reason why I dropped out gnome-shell.

---

### Post by _0R10N on 2011-06-20
BTW, updating the system didn't help at all!!!

---

### Post by bmbaker on 2011-06-20
what i found wked the best was to do a full install of natty with all the updates then add the gnome3 ppa
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell gnome-session
```
 do the update and then install gnome-shell and gnome-session then reboot and login into gnome-shell "Gnome" and do a full dist-upgrade
```
sudo apt-get update && sudo apt-get dist-upgrade
```

 reboot and then log back into gnome-shell,
 next add rico's testing ppa.

```
sudo add-apt-repository ppa:ricotz/testing
sudo apt-get update && sudo apt-get dist-upgrade
```

then fire up synaptic and install the gnome-themes gnome-extensions gnome-tweak etc etc 

only had a few minor problems but the constant updating keeps everything running well :-)

I also upgraded my kernel to:```
http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/
```


```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/linux-headers-3.0.0-0300rc2-generic_3.0.0-0300rc2.201106081532_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/linux-headers-3.0.0-0300rc2_3.0.0-0300rc2.201106081532_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc2-oneiric/linux-image-3.0.0-0300rc2-generic_3.0.0-0300rc2.201106081532_i386.deb
sudo dpkg -i *.deb
```

everything runs sweet :-)

---


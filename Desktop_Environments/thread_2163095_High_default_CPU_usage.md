---
title: "High default CPU usage"
date: 2013-07-17
forum: Desktop Environments
---

### Post by yogyakor on 2013-07-17
I have installed Lubuntu 13.04 on a generic Core3 desktop. It was running well for a few days, but now I experience a very high default CPU usage. I've tried booting into previous version of kernel and uninstalled some software, all to no avail. Any suggestions on how to get CPU down to normal?

```
top - 13:54:05 up 15 min,  2 users,  load average: 1,41, 1,51, 1,07
Tasks: 156 total,   2 running, 154 sleeping,   0 stopped,   0 zombie
%Cpu(s): 18,8 us, 15,6 sy,  0,0 ni, 65,2 id,  0,3 wa,  0,0 hi,  0,1 si,  0,0 st
KiB Mem:   1740160 total,   843836 used,   896324 free,    34064 buffers
KiB Swap:  1790972 total,        0 used,  1790972 free,   620632 cached


  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
  868 syslog    20   0 32340 3468 1100 S   9,0  0,2   1:19.54 rsyslogd          
  958 messageb  20   0  3656 1512  968 S   7,0  0,1   1:00.43 dbus-daemon       
 1340 darmayud  20   0 71252 6936 5612 S   4,7  0,4   0:42.76 lxsession         
10894 darmayud  20   0  534m  80m  45m S   4,7  4,7   0:46.20 chromium-browse   
 1201 root      20   0 27396 4724 3360 S   4,0  0,3   0:34.57 polkitd           
 1191 root      20   0 89908  27m  21m S   3,0  1,6   0:29.08 Xorg              
 1196 root      20   0 44360 6040 5052 S   2,3  0,3   0:21.29 NetworkManager    
 1449 darmayud  20   0  283m  16m  12m S   2,3  1,0   0:23.45 nm-applet         
 1673 root      20   0 28864 3772 3084 S   2,3  0,2   0:19.09 upowerd           
  988 root      20   0  7512 2908 2292 S   2,0  0,2   0:17.49 modem-manager     
 1265 root      20   0 34376 3404 2780 S   2,0  0,2   0:17.80 console-kit-dae   
 1435 darmayud  20   0 61072 4428 3160 S   1,7  0,3   0:18.02 xfce4-power-man   
 1426 darmayud  20   0  101m  10m 6364 S   1,3  0,6   0:09.89 conky           

```

---

### Post by TenPlus1 on 2013-07-17
You would have to supply a little more information, is it a Core i3 desktop ? what graphics card ? 32-bit or 64-bit ubuntu ? what software have you installed and removed ?

---

### Post by yogyakor on 2013-07-17
Sure, it is a Corei3 desktop with generic Intel graphics card. The machine itself is 64bit but I installed 32-bit Lubuntu on it. 

Prior to high CPU usage I have updated the system then installed Inkscape with Sozi extension, as well as 'glade' package. I have subsequently purged all of it but high CPU usage remained across several reboots.

 I have Inkscape+sozi installed on several -buntus so I think it's safe to rule that out as a possible culprit.

---


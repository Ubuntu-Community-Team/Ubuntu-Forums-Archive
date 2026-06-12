---
title: "compiz segfault error on Dell Laptop with Gnome Desktop"
date: 2018-01-07
forum: Desktop Environments
---

### Post by rioguia2 on 2018-01-07
I run Ubuntu 16.04 with the gnome desktop and it has run fine for months until yesterday.

On booting, my computer started complaining about a compiz error.  The result was that the desktop kept icons disappeared and reappeared in a cycle about every 10 seconds or so.  I was able to open a terminal during one of the cycles and downloaded the XFCE desktop which I am now running.

The first mention of the problem from the syslog looks like this:

```
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:08 MY-NAME-D630 kernel: [  351.071558] compiz[3636]:segfault at 0 ip 00007f29b63da986 sp 00007ffc0b5b7ee0 error 4 ini965_dri.so[7f29b5e02000+82d000][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:06 MY-NAME-D630 colord[905]: message repeated 2 times: [(colord:905): Cd-WARNING **: failed to get session [pid 4525]: Nosuch device or address][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:10 MY-NAME-D630 whoopsie[1023]: [15:06:10] Parsing/var/crash/_usr_bin_compiz.1000.crash.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:10 MY-NAME-D630 whoopsie[1023]: [15:06:10] Uploading/var/crash/_usr_bin_compiz.1000.crash.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:11 MY-NAME-D630 whoopsie[1023]: [15:06:11] Sent; serverreplied with: No error[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:11 MY-NAME-D630 whoopsie[1023]: [15:06:11] Response code: 200[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:11 MY-NAME-D630 whoopsie[1023]: [15:06:11] Reported OOPS ID0a41892c-f31d-11e7-9e0d-fa163e192766[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Jan 6 15:06:20 MY-NAME-D630 kernel: [  362.464112][drm:drm_atomic_helper_commit_cleanup_done [drm_kms_helper]] *ERROR*[CRTC:34:pipe B] flip_done timed out[/FONT][/COLOR]
Jan 6 15:06:20 MY-NAME-D630 kernel: [  362.568074] ------------[ cuthere ]-----------
```

My Hardware is
 ```

inxf -Fx
 
System:   Host:MYNAME-Latitude-D630 Kernel:4.10.0-42-generic x86_64 (64 bit gcc:5.4.0)
          Desktop:Xfce 4.12.3 (Gtk 2.24.28) Distro:Ubuntu 16.04 xenial
Machine:  System:Dell (portable) product:Latitude D630
          Mobo:Dell model:0KU184 Bios:Dell v:A02 date:06/07/2007
CPU:      Dual coreIntel Core2 Duo T7100 (-MCP-)cache:2048 KB
          flags:(lm nx sse sse2 sse3 ssse3 vmx) bmips:7179
          clock speeds:max:1801 MHz 1:1200 MHz 2:1200 MHz
Graphics: Card:Intel Mobile GM965/GL960 Integrated Graphics Controller (primary)
          bus-ID:00:02.0
          Display Server:X.Org 1.19.5 drivers:(unloaded: fbdev,vesa)
          Resolution:1280x800@59.98hz
          GLX Renderer:Mesa DRI Intel 965GM
          GLX Version:2.1 Mesa 17.2.4 Direct Rendering:Yes
Audio:    CardIntel 82801H (ICH8 Family) HD Audio Controller
          driver:snd_hda_intel bus-ID:00:1b.0
          Sound:Advanced Linux Sound Architecture v:k4.10.0-42-generic
Network:  Card-1:Broadcom NetXtreme BCM5755M Gigabit Ethernet PCI Express
          driver:tg3 v:3.137 bus-ID:09:00.0
          IF:enp9s0 state:down mac:00:00:00:00:00:00
          Card-2:Broadcom BCM4311 802.11b/g WLAN
          driver:b43-pci-bridge bus-ID:0c:00.0
          IF:wlan0 state:up mac:00:00:00:00:00:00
Drives:   HDD Total Size:500.1GB (34.9% used)
          ID-1:/dev/sda model:WDC_WD5000LPVX size:500.1GB temp:37C
Partition:ID-1:/ size:456G used:161G (38%) fs:ext4 dev:/dev/sda1
          ID-2:swap-1 size:2.67GB used:0.04GB (2%) fs:swap dev:/dev/sda5
RAID:     No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:  System Temperatures: cpu:52.0C mobo:N/A
          Fan Speeds (in rpm): cpu:N/A
Info:     Processes:196 Uptime:5:36 Memory:1512.6/2492.9MB
          Init:systemd runlevel:5 Gcc sys:5.4.0
          Client:Shell (bash 4.3.481) inxi:2.2.3

```

---

### Post by deadflowr on 2018-01-07
Looks like you might be effected by this bug
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1741447]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1741447")
Or a variant of it
Ongoing discussion (non-support) here:
[https://community.ubuntu.com/t/mesa-17-2-4-broke-unity-for-older-generation-intel/3180]("https://community.ubuntu.com/t/mesa-17-2-4-broke-unity-for-older-generation-intel/3180")
seems to be an issue with intel drivers.

---


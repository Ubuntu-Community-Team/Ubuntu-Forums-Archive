---
title: "GeForce GT 325M on Ubuntu 10.04 warining"
date: 2010-05-01
forum: Desktop Environments
---

### Post by kretes on 2010-05-01
Hi all,

I've tried 10.04 amd64 on Asus N71JV with GeForce GT 325M

Installation was ok. Afterwards also, but it occurred to me, that I can't change to text TTY with ctrl+alt+f1 and others. I've used the internal function to install nvidia drivers, and so I did, however X windows hasn't started after that.

In the Xorg.1.log I had 
"(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log
"

I was desperated to keep my installation, so I've installed another 10.04 on another partition and diff-ed configuration files to remove nvidia drivers.

I've removed this files  from etc:
razem 8
drwx------ 1 tomasz tomasz    0 2010-05-01 11:33 .
drwx------ 1 tomasz tomasz 4096 2010-05-01 21:40 ..
drwx------ 1 tomasz tomasz 4096 2010-05-01 11:30 alternatives
drwx------ 1 tomasz tomasz    0 2010-05-01 11:32 modprobe.d
drwx------ 1 tomasz tomasz    0 2010-05-01 11:33 X11
drwx------ 1 tomasz tomasz    0 2010-05-01 11:33 xdg

./alternatives:
razem 52342
drwx------ 1 tomasz tomasz     4096 2010-05-01 11:30 .
drwx------ 1 tomasz tomasz        0 2010-05-01 11:33 ..
lrwxrwxrwx 1 tomasz tomasz      104 2010-05-01 11:28 libvdpau_nvidia.so -> /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so
lrwxrwxrwx 1 tomasz tomasz      108 2010-05-01 11:28 libvdpau_nvidia.so.1 -> /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.1
lrwxrwxrwx 1 tomasz tomasz      110 2010-05-01 11:29 man_nvidiaxconfig.gz -> /usr/share/man/man1/alt-nvidia-current-xconfig.1.gz
lrwxrwxrwx 1 tomasz tomasz      108 2010-05-01 11:28 nvidia-autostart.desktop -> /usr/share/nvidia-current/nvidia-autostart.desktop
lrwxrwxrwx 1 tomasz tomasz      104 2010-05-01 11:28 nvidia_bug_report -> /usr/lib/nvidia-current/bin/nvidia-bug-report.sh
lrwxrwxrwx 1 tomasz tomasz      120 2010-05-01 11:28 nvidia_desktop -> /usr/share/nvidia-current/ubuntu-nvidia-settings.desktop
lrwxrwxrwx 1 tomasz tomasz       92 2010-05-01 11:28 nvidia_drv -> /usr/lib/nvidia-current/xorg/nvidia_drv.so
lrwxrwxrwx 1 tomasz tomasz       74 2010-05-01 11:28 nvidia_modconf -> /lib/nvidia-current/modprobe.conf
lrwxrwxrwx 1 tomasz tomasz       84 2010-05-01 11:28 nvidia_smi -> /usr/lib/nvidia-current/bin/nvidia-smi
lrwxrwxrwx 1 tomasz tomasz      102 2010-05-01 11:28 nvidia-smi.1.gz -> /usr/share/man/man1/alt-nvidia-current-smi.1.gz
lrwxrwxrwx 1 tomasz tomasz       92 2010-05-01 11:28 nvidia_xconfig -> /usr/lib/nvidia-current/bin/nvidia-xconfig
-rwxrwxrwx 1 tomasz tomasz 53587308 2010-04-11 11:29 workspace.zip
lrwxrwxrwx 1 tomasz tomasz       76 2010-05-01 11:29 xvmcconfig -> /usr/lib/nvidia-current/XvMCConfig

./modprobe.d:
razem 1
drwx------ 1 tomasz tomasz  0 2010-05-01 11:32 .
drwx------ 1 tomasz tomasz  0 2010-05-01 11:33 ..
lrwxrwxrwx 1 tomasz tomasz 72 2010-05-01 11:32 nvidia-graphics-drivers.conf -> /etc/alternatives/nvidia_modconf

./X11:
razem 2
drwx------ 1 tomasz tomasz   0 2010-05-01 11:33 .
drwx------ 1 tomasz tomasz   0 2010-05-01 11:33 ..
-rwxrwxrwx 1 tomasz tomasz 269 2010-04-30 19:51 xorg.conf
-rwxrwxrwx 1 tomasz tomasz 270 2010-04-30 19:55 xorg.conf.failsafe
-rwxrwxrwx 1 tomasz tomasz 216 2010-04-30 14:50 xorg.conf.nvidia

./xdg:
razem 0
drwx------ 1 tomasz tomasz 0 2010-05-01 11:33 .
drwx------ 1 tomasz tomasz 0 2010-05-01 11:33 ..
drwx------ 1 tomasz tomasz 0 2010-05-01 11:34 autostart

./xdg/autostart:
razem 1
drwx------ 1 tomasz tomasz  0 2010-05-01 11:34 .
drwx------ 1 tomasz tomasz  0 2010-05-01 11:33 ..
lrwxrwxrwx 1 tomasz tomasz 92 2010-05-01 11:34 nvidia-autostart.desktop -> /etc/alternatives/nvidia-autostart.desktop

and X system loaded. It's a shame that ubuntu is proposing something that is not appropriate - It was version "195.36.15-0ubuntu2" of nvidia-current package.
Right now I can see that nvidia has 195.36.24 version available so after backup I will try to install that and let you know.

However maybe somebody has an idea why the text terminals aren't working, and what to check - whiHi all,

I've tried 10.04 amd64 on Asus N71JV with GeForce GT 325M

Installation was ok. Afterwards also, but it occurred to me, that I  can't change to text TTY with ctrl+alt+f1 and others. I've used the  internal function to install nvidia drivers, and so I did, however X  windows hasn't started after that.
In the Xorg.1.log I had 
"(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.1.log" for additional  information.

 ddxSigGiveUp: Closing log
"

I've was desperated to keep my installation, so I've installed another  10.04 on another partition and diffed configuration files to remove  nvidia drivers.

I've removed this files  from etc:
razem 8
drwx------ 1 tomasz tomasz    0 2010-05-01 11:33 .
drwx------ 1 tomasz tomasz 4096 2010-05-01 21:40 ..
drwx------ 1 tomasz tomasz 4096 2010-05-01 11:30 alternatives
drwx------ 1 tomasz tomasz    0 2010-05-01 11:32 modprobe.d
drwx------ 1 tomasz tomasz    0 2010-05-01 11:33 X11
drwx------ 1 tomasz tomasz    0 2010-05-01 11:33 xdg

./alternatives:
razem 52342
drwx------ 1 tomasz tomasz     4096 2010-05-01 11:30 .
drwx------ 1 tomasz tomasz        0 2010-05-01 11:33 ..
lrwxrwxrwx 1 tomasz tomasz      104 2010-05-01 11:28 libvdpau_nvidia.so  -> /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so
lrwxrwxrwx 1 tomasz tomasz      108 2010-05-01 11:28  libvdpau_nvidia.so.1 ->  /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.1
lrwxrwxrwx 1 tomasz tomasz      110 2010-05-01 11:29  man_nvidiaxconfig.gz ->  /usr/share/man/man1/alt-nvidia-current-xconfig.1.gz
lrwxrwxrwx 1 tomasz tomasz      108 2010-05-01 11:28  nvidia-autostart.desktop ->  /usr/share/nvidia-current/nvidia-autostart.desktop
lrwxrwxrwx 1 tomasz tomasz      104 2010-05-01 11:28 nvidia_bug_report  -> /usr/lib/nvidia-current/bin/nvidia-bug-report.sh
lrwxrwxrwx 1 tomasz tomasz      120 2010-05-01 11:28 nvidia_desktop  -> /usr/share/nvidia-current/ubuntu-nvidia-settings.desktop
lrwxrwxrwx 1 tomasz tomasz       92 2010-05-01 11:28 nvidia_drv ->  /usr/lib/nvidia-current/xorg/nvidia_drv.so
lrwxrwxrwx 1 tomasz tomasz       74 2010-05-01 11:28 nvidia_modconf  -> /lib/nvidia-current/modprobe.conf
lrwxrwxrwx 1 tomasz tomasz       84 2010-05-01 11:28 nvidia_smi ->  /usr/lib/nvidia-current/bin/nvidia-smi
lrwxrwxrwx 1 tomasz tomasz      102 2010-05-01 11:28 nvidia-smi.1.gz  -> /usr/share/man/man1/alt-nvidia-current-smi.1.gz
lrwxrwxrwx 1 tomasz tomasz       92 2010-05-01 11:28 nvidia_xconfig  -> /usr/lib/nvidia-current/bin/nvidia-xconfig
-rwxrwxrwx 1 tomasz tomasz 53587308 2010-04-11 11:29 workspace.zip
lrwxrwxrwx 1 tomasz tomasz       76 2010-05-01 11:29 xvmcconfig ->  /usr/lib/nvidia-current/XvMCConfig

./modprobe.d:
razem 1
drwx------ 1 tomasz tomasz  0 2010-05-01 11:32 .
drwx------ 1 tomasz tomasz  0 2010-05-01 11:33 ..
lrwxrwxrwx 1 tomasz tomasz 72 2010-05-01 11:32  nvidia-graphics-drivers.conf -> /etc/alternatives/nvidia_modconf

./X11:
razem 2
drwx------ 1 tomasz tomasz   0 2010-05-01 11:33 .
drwx------ 1 tomasz tomasz   0 2010-05-01 11:33 ..
-rwxrwxrwx 1 tomasz tomasz 269 2010-04-30 19:51 xorg.conf
-rwxrwxrwx 1 tomasz tomasz 270 2010-04-30 19:55 xorg.conf.failsafe
-rwxrwxrwx 1 tomasz tomasz 216 2010-04-30 14:50 xorg.conf.nvidia

./xdg:
razem 0
drwx------ 1 tomasz tomasz 0 2010-05-01 11:33 .
drwx------ 1 tomasz tomasz 0 2010-05-01 11:33 ..
drwx------ 1 tomasz tomasz 0 2010-05-01 11:34 autostart

./xdg/autostart:
razem 1
drwx------ 1 tomasz tomasz  0 2010-05-01 11:34 .
drwx------ 1 tomasz tomasz  0 2010-05-01 11:33 ..
lrwxrwxrwx 1 tomasz tomasz 92 2010-05-01 11:34 nvidia-autostart.desktop  -> /etc/alternatives/nvidia-autostart.desktop

and X system loaded. It's a shame that ubuntu is proposing something  that is not appropriate - It was version "195.36.15-0ubuntu2" of  nvidia-current package.
Right now I can see that nvidia has 195.36.24 version available so after  backup I will try to install that and let you know.

Switching to other terminal is actually working, but it isn't displaying anything, it just freeze current state of X session, but when i type username, enter, and password I am able to do anything - blindly.
However maybe somebody has an idea why the text terminals aren't  working, and what to check?
which log file, etc...

---


---
title: "Xrandr not working after update"
date: 2018-10-23
forum: Desktop Environments
---

### Post by thisismyaccount on 2018-10-23
Hello,

I have a fresh install of the standard Ubuntu 18.04, 4.15.0-36-generic that I've been using for about a month. Yesterday I updated the packages below, and xrandr stopped working for resizing output to my second monitor. I have had no issues with xrandr until this point:

```
&#9584;&#9472;$ xrandr --output eDP-1 --auto --output DP-2 --auto --panning 3840x2160+3000+0 --scale 2x2 --right-of eDP-1

```


```

&#9584;&#9472;$ sed -n -e '/2018-10-22/,$p' /var/log/apt/history.log
Start-Date: 2018-10-22  19:50:23
Commandline: aptdaemon role='role-commit-packages' sender=':1.5601'
Upgrade: fdisk:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), update-manager-core:amd64 (1:18.04.11.5, 1:18.04.11.6), uuid-runtime:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), libfdisk1:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), friendly-recovery:amd64 (0.2.38, 0.2.38ubuntu1), apturl-common:amd64 (0.5.2ubuntu14, 0.5.2ubuntu14.2), grub-common:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), libmount1:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), update-manager:amd64 (1:18.04.11.5, 1:18.04.11.6), google-chrome-stable:amd64 (69.0.3497.100-1, 70.0.3538.67-1), util-linux:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), grub2-common:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), grub-pc:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), apturl:amd64 (0.5.2ubuntu14, 0.5.2ubuntu14.2), mount:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), grub-pc-bin:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), libblkid1:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), ubuntu-drivers-common:amd64 (1:0.5.2, 1:0.5.2.1), grub-efi-amd64-bin:amd64 (2.02-2ubuntu8.4, 2.02-2ubuntu8.6), python3-distupgrade:amd64 (1:18.04.26, 1:18.04.27), python3-update-manager:amd64 (1:18.04.11.5, 1:18.04.11.6), gir1.2-snapd-1:amd64 (1.41-0ubuntu0.18.04.1, 1.43-0ubuntu0.18.04.1), ubuntu-release-upgrader-core:amd64 (1:18.04.26, 1:18.04.27), libuuid1:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), libsmartcols1:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), rfkill:amd64 (2.31.1-0.4ubuntu3.1, 2.31.1-0.4ubuntu3.2), shim-signed:amd64 (1.34.9.2+13-0ubuntu2, 1.37~18.04.2+15+1533136590.3beb971-0ubuntu1), bsdutils:amd64 (1:2.31.1-0.4ubuntu3.1, 1:2.31.1-0.4ubuntu3.2), ubuntu-release-upgrader-gtk:amd64 (1:18.04.26, 1:18.04.27), grub-efi-amd64-signed:amd64 (1.93.5+2.02-2ubuntu8.4, 1.93.7+2.02-2ubuntu8.6), libsnapd-glib1:amd64 (1.41-0ubuntu0.18.04.1, 1.43-0ubuntu0.18.04.1), shim:amd64 (13-0ubuntu2, 15+1533136590.3beb971-0ubuntu1)
End-Date: 2018-10-22  19:50:57

```

I'm guessing it is tied to one of these updates, since that is the only system change. I can execute the xrandr command without error, but nothing happens anymore. Any clues about which package may have done this from that list (and how to roll back or resolve it)? 

Thank you.

EDIT:
This was a silly mistake. There are two usb-c ports next to each other where the hdmi dongle can be attached. These were swapped and DP-2 became DP-1.

---


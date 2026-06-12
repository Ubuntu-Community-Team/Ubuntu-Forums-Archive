---
title: "Ubuntu 14.04 to 16.04 Radeon HD 5770 but basic display functionality does not work"
date: 2016-08-09
forum: Desktop Environments
---

### Post by gebbione on 2016-08-09
Lets start by saying that i wish I had read this before and I wish that on an upgrade prompt Ubuntu would warn about major compatibility issues such as -[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
however based on this page - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) my gpu should work just fine with the 16.04 drivers
So, I have just upgraded from 14.04 to 16.04 and my two screens are not detected and mirroring instead of extending the desktop.
```
$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 400, current 1280 x 1024, maximum 1280 x 1024
default connected primary 1280x1024+0+0 0mm x 0mm
   1280x1024      0.00* 
   1280x960       0.00  
   1152x864       0.00  
   1024x768       0.00  
   800x600        0.00  
   640x480        0.00  
   720x400        0.00

```
Also the resolution is too low and monitor instead of the two connected are detected as **default**. On IRC #ubuntu I have got the suggestion to configure xorg and looking at the guide at[http://zeroset.mnim.org/2013/01/07/dual-head-monitor-setup-on-ubuntu-linux-with-xorg-and-radeon/](http://zeroset.mnim.org/2013/01/07/dual-head-monitor-setup-on-ubuntu-linux-with-xorg-and-radeon/) I see that xrandr is supposed to detect the monitors well to attempt a Xorg config.
From Xorg log - Segmentation fault
```
[  5786.223] (**) ModulePath set to "/usr/lib/xorg/modules"
[  5786.223] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  5786.223] (WW) Disabling Mouse0
[  5786.223] (WW) Disabling Keyboard0
[  5786.223] (II) [KMS] drm report modesetting isn't supported.
[  5786.223] (EE) 
[  5786.223] (EE) Backtrace:
[  5786.223] (EE) 0: /usr/lib/xorg/Xorg (xorg_backtrace+0x4e) [0x5581fdedc5ce]
[  5786.223] (EE) 1: /usr/lib/xorg/Xorg (0x5581fdd2a000+0x1b6959) [0x5581fdee0959]
[  5786.223] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7fcc5f18c000+0x354a0) [0x7fcc5f1c14a0]
[  5786.223] (EE) 
[  5786.223] (EE) Segmentation fault at address 0x0
[  5786.223] (EE) 
Fatal server error:
[  5786.223] (EE) Caught signal 11 (Segmentation fault). Server aborting
[  5786.223] (EE) 
[  5786.223] (EE) 
Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
```
I dont need 3D acceleration and would like to fix the problem instead of downgrading to 14.04. What else can I try?

---

### Post by QIII on 2016-08-09
Please do not cut and paste Stack Exchange table formatting and up/downvote information.  Please have the courtesy to create a new thread here in its entirety rather than just dragging something from elsewhere.

Thanks.



With regard to your issue:  Did you have fglrx installed in 14.04 prior to upgrading and did you first uninstall it?

---

### Post by gebbione on 2016-08-10
> **QIII said:**
> With regard to your issue:  Did you have fglrx installed in 14.04 prior to upgrading and did you first uninstall it?

I have not tried removing it but the change in experience tells me something has taken over but I might be wrong. So to confirm it I have run the command shown in this thread to collect info on current VGA drivers

[http://askubuntu.com/questions/28033/how-to-check-the-information-of-current-installed-video-drivers](http://askubuntu.com/questions/28033/how-to-check-the-information-of-current-installed-video-drivers)

lspci | grep VGA ; lsmod | grep "kms\|drm" ; find /dev -group video ; \
cat /proc/cmdline ; find /etc/modprobe.d/; cat /etc/modprobe.d/*kms* ; \
ls /etc/X11/xorg.conf ; glxinfo | grep -i "vendor\|rendering" ; \
grep LoadModule /var/log/Xorg.0.log

And I get

```
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 5770]
/dev/video0
BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic root=UUID=315979a7-13a8-49cf-bd7a-616f29ad8c79 ro acpi=force nomodeset
/etc/modprobe.d/
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/mlx4.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/osspd.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/fglrx-core.conf
/etc/modprobe.d/fbdev-blacklist.conf
/etc/modprobe.d/dkms.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/oss-compat.conf
/etc/modprobe.d/vmwgfx-fbdev.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/alsa-base.conf
# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.
ls: cannot access '/etc/X11/xorg.conf': No such file or directory
direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
    Vendor: VMware, Inc. (0xffffffff)
OpenGL vendor string: VMware, Inc.
[ 21038.259] (II) LoadModule: "glx"
[ 21038.266] (II) LoadModule: "ati"
[ 21038.267] (II) LoadModule: "radeon"
[ 21038.268] (II) LoadModule: "modesetting"
[ 21038.268] (II) LoadModule: "fbdev"
[ 21038.269] (II) LoadModule: "vesa"
[ 21038.274] (II) LoadModule: "fbdevhw"
[ 21038.274] (II) LoadModule: "fbdevhw"
[ 21038.274] (II) LoadModule: "vbe"
[ 21038.275] (II) LoadModule: "int10"
[ 21038.323] (II) LoadModule: "ddc"
[ 21038.441] (II) LoadModule: "shadow"
[ 21038.442] (II) LoadModule: "fb"
[ 21038.443] (II) LoadModule: "int10"
[ 21038.816] (II) LoadModule: "evdev"

```

The fglrx file is interesting in the fact that it attempts to blacklist radeon and amdgpu as shown

```
# This file was installed by fglrx""
# Do not edit this file manually


blacklist radeon
alias fglrx fglrx
alias radeon off
alias lbm-radeon off


blacklist amdgpu
alias amdgpu off
alias lbm-amdgpu off

```
I guess it is safe to remove it by just commenting out the conf and not remove the actual binary yet?
I will give it a try and come back to the forum
[B]
UPDATE: I have moved the file/changed extension but it has made no difference. I have restarted lightdm first and then also tried restarting the whole machine but I see no change[/B]

RE formatting : i thought i had removed it from the post. I am just using QUOTE to highlight the commands outputs

---

### Post by howefield on 2016-08-10
> **gebbione said:**
> RE formatting : i thought i had removed it from the post. I am just using QUOTE to highlight the commands outputs

Better to use code tags to preserve formatting from terminal output as you can see from your now edited post above.

---

### Post by gebbione on 2016-08-11
In my case it was not a problem with compatibility between drivers/cards and kernel. I had nomodeset in my grub config blocking radeon driver from loading.


to check grub config see this article - [http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/](http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/)


So in my experience after looking at this problem try the following


1 - check modprobe config to make sure the correct driver is blacklisted/or not,under /etc/modprobe.d/ files and make sure radeon is not blacklisted


2 - check grub as described above and remove the nomodeset option bearing in mind that this might cause other problems

---


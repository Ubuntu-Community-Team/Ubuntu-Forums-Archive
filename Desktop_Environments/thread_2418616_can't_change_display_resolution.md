---
title: "can't change display resolution"
date: 2019-05-08
forum: Desktop Environments
---

### Post by rngdmstr on 2019-05-08
Hope someone can help.  The issue I am having is very similar to this one:  [https://ubuntuforums.org/showthread.php?t=1705929](https://ubuntuforums.org/showthread.php?t=1705929)  I've tried these steps:  [https://askubuntu.com/questions/1099262/ubuntu-18-04-1-lts-only-one-resolution-available](https://askubuntu.com/questions/1099262/ubuntu-18-04-1-lts-only-one-resolution-available)  I can add the new resolution that shows in my display settings, but I receive a "The selected configuration could not be applied" when I try to change it.  $ xrandr -s 1920x1080_60.00 Failed to change the screen configuration!  Have tried both the Xorg driver as well as the nvidia driver, same behaviour on both. I also tried changing the xorg config file to comply with the specifications of my monitor for horizontal/vertical display and that had no effect.  Really grasping at straws here. Would appreciate any help, thanks.

---

### Post by Xian on 2019-05-08
Just a shot .... but try to resolve by editing your /etc/default/grub file to include:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_GFXPAYLOAD_LINUX=1920x1080
```

Then apply the new config:

```
sudo update-grub
```

And finally reboot.

---


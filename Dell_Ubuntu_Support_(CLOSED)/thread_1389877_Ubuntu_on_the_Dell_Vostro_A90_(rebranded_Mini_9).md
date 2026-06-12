---
title: "Ubuntu on the Dell Vostro A90 (rebranded Mini 9)"
date: 2010-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nanotube on 2010-01-24
_**This post is a review and howto for the Dell Vostro a90n**_

Overall, it's a wonderful little machine. It is a full fledged computer, yet small enough to be comfortably carried around - even in a large jacket pocket.

**The problems with it are the following:**

The keyboard layout has moved some keys around, or off to the Fn key combos, so that takes a little getting used to. (A tip: while unmarked, Fn-Z and Fn-X are F11 and F12, respectively).

The wireless didn't work out of the box, with the pre-installed Dell Ubuntu 8.04.2. 

The screen only opens up to about 135 degrees (45 degrees from vertical). It would be nice to be able to open it all the way to 180, for those cases when you're standing over it and looking at it from the top.

**The nice things are:**
It is a very solidly built machine, doesn't wobble or squeak, and feels safe to pick up by a corner with one hand.

the screen is sharp and bright and is high-resolution enough to make it quite usable (1024x600), despite being only 9 inch diagonal 

the battery life is upward of 4 hours under 'normal' use.

very light and portable.

completely silent, due to the ssd hard drive

**what i had to do to get it working nicely:**

first, to get wifi to work on the old version of ubuntu that came with it, i tried installing the latest broadcom STA driver. that did get it working, however it would fail to reconnect after a suspend/resume cycle. There were some other things missing from the hardy version, namely easy config of external display, the fancy compiz visual effects, the up to date packages. (for instance, firefox was still on version 3.0.14, even though at the time the latest 3.0 patch was 3.0.17 - not safe). also, the architecture used was 'lpia', which prevented normal use of most third-party repositories which usually support either i386 or amd64, but not lpia.

so, while it's possible to keep using the 'dellbuntu' hardy on the machine, i highly recommend an install of the latest ubuntu release. i upgraded the machine to the stock ubuntu karmic desktop version (not the netbook remix, because i prefer it to act as a normal computer, so the netbook interface would be useless to me anyway.)

i created a usb bootable disk out of the cd image, using usb-creator, booted from it and tested to see if the hardware works. neither the sound nor the wifi worked out of the box  on the karmic livecd, but after some research i found:

the fix for the sound: [http://www.ubuntumini.com/2009/11/fix-audio-on-dell-vostro-a90.html](http://www.ubuntumini.com/2009/11/fix-audio-on-dell-vostro-a90.html) (setting "options snd-hda-intel model=dell" in file "/etc/modprobe.d/alsa-base.conf"), 

and fix for the wifi (enabling the broadcom sta driver, by installing package 'bcmwl-kernel-source' and rebooting)

so i installed karmic, made the tweaks for sound and wifi, and now everything works smoothly. wifi comes up after suspend without any hiccups, sound works fine.

the following hardware has been tested to work: built-in webcam, built-in microphone, suspend/resume, bluetooth, wired ethernet, usb ports, external microphone port, sound, vga-out, touchpad, keyboard

there's a bug in xorg or compiz however, that makes the computer freeze upon the hooking up of an external monitor to extend the desktop. the simple workaround is to run metacity --replace before connecting the external monitor, to disable compiz. then everything works very nicely. 
(link to launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/419328?comments=all))

and that's that - now my a90 is a lean mean ubuntu machine. hope that helps other vostro a90 / mini 9 owners to get things up and running!

_Some additional configuration:_

I added the 'noatime' option in /etc/fstab, to reduce the load on the SSD disk (noatime means filesystem doesn't write the time of last file access every time a file is read). now my fstab line looks like this:
```
UUID=<bunch of hex> /               ext4    noatime,errors=remount-ro 0       1
```

Also, I set vm.swappiness to 0, again, to reduce the load on the SSD due to swap-writing. with vm.swappiness at 0, system won't use swap unless it absolutely has to. run command ```
sudo sysctl vm.swappiness=0
``` to set this. to make it permanent upon reboot, put in "vm.swappiness=0" in /etc/sysctl.conf.

---


---
title: "ubuntu and mice..."
date: 2006-06-04
forum: Desktop Environments
---

### Post by lukin1982 on 2006-06-04
Ubuntu is great!  I love the look, feel & simplicity.  I have one gripe, however.  Out of everything that Ubuntu is capable of doing, it's weakest point is detection of mice.  It would be helpful if Ubuntu had a way of detecting multi-button mice and automatically configuring them for users.  It is frustrating going through guides and information found in the forums and other documentation for hours on end only to find that the information is outdated or just plain wrong.

I have a logitech MediaPlay mouse.  I'm not asking for the moon here!  I don't even care if the media buttons work!  I just want my forward and back buttons to work.

I have followed the "Configuring mx500..." thread to no avail.  Can anyone point me in the right direction?

---

### Post by lukin1982 on 2006-06-04
okay... i have found a solution (on a gentoo wiki, nonetheless).  i will post this solution for the benefit of others.

once again, I have a Logitech MediaPlay Cordless USB mouse.

replace the usual mouse section of /etc/X11/xorg.conf with:
```
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "evdev"
        Option       "CorePointer"
        Option        "Dev Name"        "Logitech USB Receiver"
        Option        "Dev Phys"        "usb-*/**input0**"
        Option        "Device"        "/dev/input/**event1**"
EndSection

```

Determine the items in bold by executing:
```
cat /proc/bus/input/devices
```
and find the "Logitech USB Receiver"

Now use xmodmap to perform the following:
```
pointer = 1 3 2 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20
```

I know this is a really quick walkthrough, but maybe someone else can improve upon it.

---

### Post by ironfistchamp on 2006-06-05
I tried this and came up with problems. Got the error "Unkown protocol: evdev" on bootup

Any ideas for a fix?

Thanks

Ironfistchamp

---


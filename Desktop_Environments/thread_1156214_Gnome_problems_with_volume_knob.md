---
title: "Gnome problems with volume knob"
date: 2009-05-11
forum: Desktop Environments
---

### Post by fischer98 on 2009-05-11
This is actually independent of ubuntu 9.04, but that's where I first discovered it. Also the same in Fedora 10, OpenSUSE 11.1 and LinuxMint 7 RC, all using Gnome.

Whenever I use the volume wheel on the side of my Toshiba laptop (satellite U305-5077), the little pop up in the right corner of the screen comes up, and stays up, flashing as if I am constantly turning up the volume. I can then no longer type anything anywhere in X. I have to change to another tty and back again to get it to stop. It's as if Gnome is registering the "volume up" (or down, doesn't matter which) key stroke when I flick wheel, but it never registers the "stop changing volume" key stroke. It's like I'm holding down a key on the keyboard and it's stuck.

Does anyone have any ideas on what I can check to fix this? Thanks.

---

### Post by fischer98 on 2009-05-12
bump.

---

### Post by conchyliferous on 2009-06-12
I have the same laptop and the same problem.

Any luck fixing it?

Edit:
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/367069](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/367069)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/335201](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/335201)

> What happens for you, is that the kernel sends a volume change notification in the form of a key press, and gnome-settings-daemon interprets that key as a request to change the volume, triggering another notification from the kernel in an infinite loop. Changing the volume key bindings in GNOME preferences might be simple a workaround.

However, this did not work for me. But at least the volume knob/wheel is disabled.

---

### Post by conchyliferous on 2009-06-12
This looks like a fix:
[http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723)

---


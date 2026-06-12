---
title: "Update broke my gnome session?"
date: 2006-09-16
forum: Desktop Environments
---

### Post by ryanswan on 2006-09-16
I updated my system last night, which had ~5 updates.  It forced a reboot and since then I have the following message after I login:
"I could not start you session and so I have started the failsafe xterm session."  Prior to this update, everything was just fine.

From there I run "gnome-session" abd my system loads properly for the most part.  I'm running the nvidia drivers, which were updated, but I don't see how they are the problem since I'm here in dual-monitor 16x12 mode and the nvidia driver seems to load properly before the login splash screen.  But I'm open to suggestions.

I looked at /var/log/Xorg.0.log and see errors following:
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.

In ~/xsession-errors I see the following:
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
Sound device inadequate for esound, fatal.

I am at a loss, since I cannot repair the /dev/wacom issue even with commenting all references to it out of xorg.conf and I yanked my soundcard for the time being.

Any help will be greatly appreciated.  Thank you.

---

### Post by ryanswan on 2006-09-16
/bump

---

### Post by CromagDK on 2006-09-16
[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

Not sure if it helps. You might have looked through it.

CromagDK

---

### Post by ryanswan on 2006-09-17
> **CromagDK said:**
> [http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

Not sure if it helps. You might have looked through it.

CromagDK

I tried to do what it said but it didn't help.  I even rebuilt my kernel, new  vnidia drivers, etc.  Any more ideas? I am pretty lost at this point.

---


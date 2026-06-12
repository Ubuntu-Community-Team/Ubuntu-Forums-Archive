---
title: "Dell Inspiron 5100 wireless does not work"
date: 2011-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by motnoslo on 2011-01-10
I  am having an issue with the wireless on an Inspiron 5100. After the initial install of 11.04, the network manager applet said that the wireless device was not ready and had missing firmware. I ran lspci -nn and saw the Broadcom wireless, plus this machine previously was running XP with wireless. I then ran /usr/bin/jockey-gtk. It found the Broadcom wireless drivers and activated them, but the network manager app still said the device was not ready.

I then ran update manager and rebooted. When I logged backed in the network manager still saw the wireless as not ready with missing firmware. I ran /usr/bin/jockey-gtk again, it found the Broadcom wireless drivers again, but when I tried to activate, I get this message in a pop-up window:
SystemError: installArchives () failed

What am I missing to get the wireless to work?
The Ethernet does work fine.

Thanks,
Tom

---

### Post by Bucky Ball on 2011-01-10
Stop! Uninstall. There is no 11.04 (yet) and you've installed the problematic 10.10 kernel (it professes to be the unreleased 11.04, not due til April 2011) . Broadcom wireless cards are one of the major issues. If you are online with a cable it should be easy to get the wireless card up. 

Drop back to the last kernel or install 10.04 LTS (long term support). 10.10 has a multitude of issues right now and as a new user, avoid, and install the stable kernel; 10.04 LTS. MUCH longer support life and should give you a smoother ride until you learn the ropes. By that time, 10.10 will be fixed probably and you'll have some idea how to tackle it if you decide to go that way. ;)

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

Latest is NOT always the greatest in Linux world (or Windows world for that matter). That is a Windows myth. ;)

Having said all that: System >Administration >Additional Drivers. If you are online and can't activate that driver you have a problem with the kernel probably. You really shouldn't need to work from the command line or do anything tricky to install the drivers and firmware. It is a two click process from the desktop.

---

### Post by motnoslo on 2011-01-11
Thanks Bucky Ball, the 10.04 LTS was the way to go. installed the wireless driver, rebooted and all is well. i've been away from Linux for about 5 years, and I'm trying to turn the teenager next door on to Linux after he was given a rather suspicious behaving old Windows laptop. Thanks again.

---

### Post by Bucky Ball on 2011-01-11
Great news! No probs. If you're trying to impress, 10.04 LTS is the go. 10.10 in its current state could put a new user off. ;)

Welcome and enjoy!

---


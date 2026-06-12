---
title: "KDE 4.1 Keyboard's special keys"
date: 2008-07-31
forum: Desktop Environments
---

### Post by ger_macaco on 2008-07-31
After upgrading to KDE 4.1 from KDE 3, everything seems to be working fine, expect for the keyboard's special keys. I mean, the keys on my Genius keyboard to Play/Pause, Stop, Increase and Decrease volume.

Is there any way I can fix this?

I tried to assign this keys to the keyboard shortcuts under System Settings, but it doesn't seem to recognize them.

Many Thanks!

PS: I'm running Kubuntu 8.04 on an amd64 PC (if this is of any help)

---

### Post by labinnsw on 2009-02-26
I am having a similar problem. My Keyboard is a Genius Comfy KB-16M Series. I have selected "Genius Comfy KB-16M Series" under System > Preferences > Keyboard the Layout tab. Some of the special keys work but not all keys work as intended. When I change them in System > preferences > Keyboard shortcuts, the Fast forward and Eject keys revert after reboot. The key mapping is detailed below. Keys on left, current task on right.

rewind = Nothing
play/pause = play/pause
Stop = Stop
Fast forward = Calculator
Eject = Volume Up
Volume Down = Volume Down
Volume Up = Nothing
Volume Mute = Volume Mute
Screen Saver = Nothing
Calculator = Nothing
Email = Email
Back = Nothing
www = www
Forward = Nothing
Sleep = Standby
Wake Up = Nothing

OS = Ubuntu 8.04
Intel Core2 Quad 32 bit PC

I did try [http://ubuntuforums.org/showthread.php?t=502099]("http://ubuntuforums.org/showthread.php?t=502099") and [http://marius.scurtescu.com/2006/02/01/multimedia_keys]("http://marius.scurtescu.com/2006/02/01/multimedia_keys") but either it does not work for this version or I cannot follow it. I am getting unexpected results that I cannot make sense of.

I know this says KDE but I am hoping that what ever works, will work for Gnome and KDE.

---

### Post by labinnsw on 2009-02-26
This is a bit clearer [https://help.ubuntu.com/community/MultimediaKeys]("https://help.ubuntu.com/community/MultimediaKeys")

---

### Post by labinnsw on 2009-02-28
Ok. In the end here is what I did. I installed keytouch, keytouch-data and keytouch-editor all from synaptic. (This solution made it easy to map the keys but froze the computer on shut down or restart. I also found a solution for that which I will also include.) Key touch comes with full instructions and documentation. After installation, it can be found under System > Preferences.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg854070.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg854070.html") Explains how to fix the freezing problem, but I could not find "keytouch-config/src/callbacks.c." Luckily, it also includes a patch from Satanasinc at [https://bugs.launchpad.net/ubuntu/+source/keytouch/+bug/186713/comments/36]("https://bugs.launchpad.net/ubuntu/+source/keytouch/+bug/186713/comments/36")

I wanted to include it here but the formatting looks awkward here so it might be better to just follow the link.

Hope this will be of help to someone.

---


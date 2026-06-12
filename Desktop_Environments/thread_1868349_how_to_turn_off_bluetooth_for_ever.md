---
title: "how to turn off bluetooth for ever"
date: 2011-10-24
forum: Desktop Environments
---

### Post by outofthecave on 2011-10-24
I just found out how to stop the bluetooth daemon from loading on startup (in Gnome 3) and I wanted to share my knowledge:

1. Gain root permissions: Either login as root or "sudo bash" in a terminal.
2. Go to /etc/default: "cd /etc/default"
3. Open the file "bluetooth" with your favorite text editor, e.g. "gedit bluetooth"
4. Lines starting with "#" are comments.  Read them.
5. Replace "BLUETOOTH_ENABLED=1" by "BLUETOOTH_ENABLED=0".
6. The next time you reboot, the bluetooth daemon will not be started.

Please note that the bluetooth indicator in the top gnome panel may still show up.  To disable it, unlock the startup programs configuration (see [http://ubuntuforums.org/showthread.php?t=1795650](http://ubuntuforums.org/showthread.php?t=1795650)).  Then, go to "Applications > Other > Startup Applications" and uncheck the box next to "Bluetooth manager".

---

### Post by Truthspeaker on 2011-10-30
Thank you

---

### Post by Rodney9 on 2011-10-30
Great Tip, works in Lubuntu as well.

---

### Post by mike555 on 2011-10-30
Also works on Xubuntu 11.10

---

### Post by reset042 on 2012-04-13
I'm afraid this didn't work for me on Ubuntu 11.10. Is it possible something else is starting the blasted thing?

---


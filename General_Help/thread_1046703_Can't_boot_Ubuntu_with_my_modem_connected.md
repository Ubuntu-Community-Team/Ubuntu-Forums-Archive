---
title: "Can't boot Ubuntu with my modem connected"
date: 2009-01-21
forum: General Help
---

### Post by unb2 on 2009-01-21
It hangs on "Starting Bluetooth" while booting if I let my modem connected. Whithout it it's fine. I already tried removing the bluetooth from the boot process with the codes that I found on this thread:

[http://ubuntuforums.org/showthread.php?t=1026334](http://ubuntuforums.org/showthread.php?t=1026334)


Code:

ls -l /etc/rc*.d/*bluetooth > ~/bluetooth_symlinks
sudo update-rc.d -f bluetooth remove

But nothing happened...

Can anybody help me please? Thanks in advance.

---

### Post by unb2 on 2009-01-22
**Anybody?**

---


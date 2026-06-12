---
title: "pulseaudio and notify_osd not exiting on logout"
date: 2009-03-26
forum: Desktop Environments
---

### Post by lriis on 2009-03-26
I'm on jaunty and trying to use pam_mount. When I log out of Gnome however my $HOME is not unmounted as it should because the device is busy. I was able to get an lsof to run at umount time which yielded:
```
COMMAND     PID  USER   FD   TYPE DEVICE  SIZE   NODE NAME
pulseaudi 15085 aesop   13u   REG  252,0 13279 154739 /home/aesop/.pulse/b6cbde296d9c99bed24340b549ca4b06:device-volumes.i486-pc-linux-gnu.gdbm
pulseaudi 15085 aesop   14u   REG  252,0 12747 154740 /home/aesop/.pulse/b6cbde296d9c99bed24340b549ca4b06:stream-volumes.i486-pc-linux-gnu.gdbm
notify-os 15276 aesop    3w   REG  252,0     0  81448 /home/aesop/.cache/notify-osd.log
```

How can I make GDM (or gnome) kill all remaining processes before ending the session?

---


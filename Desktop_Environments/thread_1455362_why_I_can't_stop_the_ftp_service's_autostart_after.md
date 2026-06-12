---
title: "why I can't stop the ftp service's autostart after boot"
date: 2010-04-15
forum: Desktop Environments
---

### Post by appleorchard2000 on 2010-04-15
After I had made vsftpd unable to autostart with the command:
sudo update-rc.d vsftpd start 39 3 5 . stop 61 0 1 2 4 6 .

I found it is running again automatically after reboot.
And it is the output of sysv-rc-conf in the attachments.

the version I used is ubuntu 10.04 lucid(development branch)

---


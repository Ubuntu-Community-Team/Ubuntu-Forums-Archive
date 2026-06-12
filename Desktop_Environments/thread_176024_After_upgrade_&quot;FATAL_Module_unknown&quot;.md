---
title: "After upgrade &quot;FATAL: Module unknown&quot;"
date: 2006-05-14
forum: Desktop Environments
---

### Post by pmilin@ptt.yu on 2006-05-14
Dear ALL,
Yesterday I did upgrade of my Ubuntu 5.10. Since I have dial-up access, I used the opportunity to do it from other place with much better (permanent) connection. It was quite a bit upgrade. Among other things kernel upgraded from 2.6.12-9-686 to 2.6.12-10-686. But, after first restart, grub changed (which I know how to fix), offering me two kernels and if I selected any of them I got only FATAL ERROR message:

```
FATAL: Module unknown not found.
mount: Mounting /dev/hda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

I tried to fix grub with Ubuntu Live CD:
```
sudo grub
find /boot/grub/stage1
root (hd0,1)
setup (hd0)
quit
```
Noting happened.

Please, help me I am quite desperate, since I have lots of data on my Linux partition and some of it is a result of collaboration with other people.
I didn't know that upgrade could be 'risky business'!

[email]pmilin@ptt.yu[/email]

---


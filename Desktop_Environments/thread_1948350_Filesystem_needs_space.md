---
title: "Filesystem needs space"
date: 2012-03-28
forum: Desktop Environments
---

### Post by pavi_elex on 2012-03-28
My filesystem is running out of space. There is only 2GB space remaining. The filesystem has 22 GB space.
Here is summary of sudo du -hs /*
6.7M    /bin
98M    /boot
4.0K    /connection.php
548K    /dev
23M    /etc
49M    /home
0    /initrd.img
0    /initrd.img.old
686M    /lib
4.0K    /lost+found
85G    /media
3.3G    /opt
0    /proc
6.3G    /root
7.9M    /sbin
4.0K    /selinux
0    /sys
92K    /tmp
6.4G    /usr
4.0K    /validitycheck.php
1.3G    /var
0    /vmlinuz
0    /vmlinuz.old

Please suggest to remove items from /root, /usr & /var.
in /root there is .local -> share --> tracker --> Data --> tracker-store.journal
tracker-store.journal is 1.5 GB file.
root --> .cpan is 260MB
root --> .cache is 486 MB

Please suggest to make some space.

---


---
title: "gvfsd causing problems with image creation"
date: 2008-09-08
forum: Desktop Environments
---

### Post by cronos4d on 2008-09-08
I am trying to create an image with the moblin image creator (moblin.org) but I am getting the following error:

Any ideas why gvfsd is getting in the way and if I can disable it?
What does it do?

Hi Matthew,

Perhaps gvfs-fuse-daemon is monitoring some mountpoints.
It needs to kill gvfs process or umount ~/.gvfs.

I'm not sure gvfs more details. But you don't practical use gvfs, it should kill or umount.

Thanks,

========================================
  Mitsutaka Amano
  MIRACLE LINUX CORPORATION
========================================



Matthew Sacks wrote:
> Mitsutaka,
> I tried your suggestion, thank you. Although I am still getting errors.
> Here is the stack trace:
>
> Sleeping for 5 seconds, try 7 of 8
> umount: /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/tmp:
> device is busy
> umount: /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/tmp:
> device is busy
> umount: 
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/share/pdk:
> not mounted
> umount: /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/pts:
> not mounted
> umount: /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/proc:
> not mounted
> umount: /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/sys: not
> mounted
> umount: 
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/var/cache/apt/ar
> chives: not mounted
> umount: /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/tmp:
> device is busy
> umount: /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/tmp:
> device is busy
> Failed to umount FileSystem directory:
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/tmp
> Execing: lsof | grep
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/tmp
> lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system
> /home/msacks/.gvfs
>       Output information may be incomplete.
> Sleeping for 5 seconds, try 8 of 8
> Failed to umount target:
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> Execing: lsof | grep
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system
> /home/msacks/.gvfs
>       Output information may be incomplete.
> dbus-daem 12089       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> dbus-daem 12089       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> dbus-daem 12089       root  txt       REG        8,1   305652      54989
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/bin/dbus-dae
> mon
> dbus-daem 12089       root  mem       REG        8,1    38412      36091
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_files
> -2.7.so
> dbus-daem 12089       root  mem       REG        8,1    34352      36098
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_nis-2
> 7.so
> dbus-daem 12089       root  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> dbus-daem 12089       root  mem       REG        8,1    26340      35919
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_compa
> t-2.7.so
> dbus-daem 12089       root  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> dbus-daem 12089       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> dbus-daem 12089       root  mem       REG        8,1   112330      36097
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpthread-2
> 7.so
> dbus-daem 12089       root  mem       REG        8,1    91852      36172
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libselinux.s
> o.1
> dbus-daem 12089       root  mem       REG        8,1   134500     228534
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libexpat
> so.1.5.2
> dbus-daem 12089       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> dbus-daem 12089       root    0u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 12089       root    1u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 12089       root    2u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 12089       root    4u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 12399       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> dbus-daem 12399       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> dbus-daem 12399       root  txt       REG        8,1   305652      54989
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/bin/dbus-dae
> mon
> dbus-daem 12399       root  mem       REG        8,1    38412      36091
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_files
> -2.7.so
> dbus-daem 12399       root  mem       REG        8,1    34352      36098
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_nis-2
> 7.so
> dbus-daem 12399       root  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> dbus-daem 12399       root  mem       REG        8,1    26340      35919
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_compa
> t-2.7.so
> dbus-daem 12399       root  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> dbus-daem 12399       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> dbus-daem 12399       root  mem       REG        8,1   112330      36097
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpthread-2
> 7.so
> dbus-daem 12399       root  mem       REG        8,1    91852      36172
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libselinux.s
> o.1
> dbus-daem 12399       root  mem       REG        8,1   134500     228534
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libexpat
> so.1.5.2
> dbus-daem 12399       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> dbus-daem 12399       root    0u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 12399       root    1u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 12399       root    2u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 12399       root    4u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> console-k 12620       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> console-k 12620       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> console-k 12620       root  txt       REG        8,1    77016      45453
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/sbin/console
> -kit-daemon
> console-k 12620       root  mem       REG        8,1    42700      36174
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libgcc_s.so
> 1
> console-k 12620       root  mem       REG        8,1    38412      36091
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_files
> -2.7.so
> console-k 12620       root  mem       REG        8,1    34352      36098
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_nis-2
> 7.so
> console-k 12620       root  mem       REG        8,1    26340      35919
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_compa
> t-2.7.so
> console-k 12620       root  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> console-k 12620       root  mem       REG        8,1   157820      36684
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libpcre
> so.3.12.1
> console-k 12620       root  mem       REG        8,1    91852      36172
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libselinux.s
> o.1
> console-k 12620       root  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> console-k 12620       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> console-k 12620       root  mem       REG        8,1   112330      36097
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpthread-2
> 7.so
> console-k 12620       root  mem       REG        8,1   707884      36689
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libglib-
> 2.0.so.0.1600.3
> console-k 12620       root  mem       REG        8,1    30624      36107
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/librt-2.7.so
> console-k 12620       root  mem       REG        8,1    14104      36692
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libgthre
> ad-2.0.so.0.1600.3
> console-k 12620       root  mem       REG        8,1   237264      36691
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libgobje
> ct-2.0.so.0.1600.3
> console-k 12620       root  mem       REG        8,1   206428      36482
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libdbus-
> 1.so.3.4.0
> console-k 12620       root  mem       REG        8,1   102304     228590
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libdbus-
> glib-1.so.2.1.0
> console-k 12620       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> console-k 12620       root    0u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> console-k 12620       root    1u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> console-k 12620       root    2u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> console-k 12620       root    4u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> console-k 12620       root   11r      CHR        5,1               35405
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/console
> dbus-daem 14019      hplip  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> dbus-daem 14019      hplip  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> dbus-daem 14019      hplip  txt       REG        8,1   305652      54989
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/bin/dbus-dae
> mon
> dbus-daem 14019      hplip  mem       REG        8,1    38412      36091
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_files
> -2.7.so
> dbus-daem 14019      hplip  mem       REG        8,1    34352      36098
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_nis-2
> 7.so
> dbus-daem 14019      hplip  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> dbus-daem 14019      hplip  mem       REG        8,1    26340      35919
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_compa
> t-2.7.so
> dbus-daem 14019      hplip  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> dbus-daem 14019      hplip  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> dbus-daem 14019      hplip  mem       REG        8,1   112330      36097
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpthread-2
> 7.so
> dbus-daem 14019      hplip  mem       REG        8,1    91852      36172
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libselinux.s
> o.1
> dbus-daem 14019      hplip  mem       REG        8,1   134500     228534
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libexpat
> so.1.5.2
> dbus-daem 14019      hplip  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> dbus-daem 14019      hplip    0u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 14019      hplip    1u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 14019      hplip    2u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> dbus-daem 14019      hplip    4u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> NetworkMa 14050       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> NetworkMa 14050       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> NetworkMa 14050       root  txt       REG        8,1    15072      46239
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/sbin/Network
> ManagerDispatcher
> NetworkMa 14050       root  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> NetworkMa 14050       root  mem       REG        8,1   157820      36684
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libpcre
> so.3.12.1
> NetworkMa 14050       root  mem       REG        8,1    91852      36172
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libselinux.s
> o.1
> NetworkMa 14050       root  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> NetworkMa 14050       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> NetworkMa 14050       root  mem       REG        8,1   112330      36097
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpthread-2
> 7.so
> NetworkMa 14050       root  mem       REG        8,1   707884      36689
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libglib-
> 2.0.so.0.1600.3
> NetworkMa 14050       root  mem       REG        8,1    30624      36107
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/librt-2.7.so
> NetworkMa 14050       root  mem       REG        8,1    14104      36692
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libgthre
> ad-2.0.so.0.1600.3
> NetworkMa 14050       root  mem       REG        8,1   237264      36691
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libgobje
> ct-2.0.so.0.1600.3
> NetworkMa 14050       root  mem       REG        8,1   206428      36482
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libdbus-
> 1.so.3.4.0
> NetworkMa 14050       root  mem       REG        8,1   102304     228590
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libdbus-
> glib-1.so.2.1.0
> NetworkMa 14050       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> NetworkMa 14050       root    0u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> NetworkMa 14050       root    1u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> NetworkMa 14050       root    2u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> system-to 14065       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> system-to 14065       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> system-to 14065       root  txt       REG        8,1    19772     253067
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/bin/system-t
> ools-backends
> system-to 14065       root  mem       REG        8,1   157820      36684
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libpcre
> so.3.12.1
> system-to 14065       root  mem       REG        8,1   134500     228534
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libexpat
> so.1.5.2
> system-to 14065       root  mem       REG        8,1   112330      36097
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpthread-2
> 7.so
> system-to 14065       root  mem       REG        8,1    91852      36172
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libselinux.s
> o.1
> system-to 14065       root  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> system-to 14065       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> system-to 14065       root  mem       REG        8,1   707884      36689
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libglib-
> 2.0.so.0.1600.3
> system-to 14065       root  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> system-to 14065       root  mem       REG        8,1     9968      36690
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libgmodu
> le-2.0.so.0.1600.3
> system-to 14065       root  mem       REG        8,1   237264      36691
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libgobje
> ct-2.0.so.0.1600.3
> system-to 14065       root  mem       REG        8,1   370972      36688
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libgio-2
> 0.so.0.0.0
> system-to 14065       root  mem       REG        8,1   206428      36482
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libdbus-
> 1.so.3.4.0
> system-to 14065       root  mem       REG        8,1    84436     229681
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libpolki
> t.so.2.0.0
> system-to 14065       root  mem       REG        8,1    25296     229683
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libpolki
> t-dbus.so.2.0.0
> system-to 14065       root  mem       REG        8,1   102304     228590
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libdbus-
> glib-1.so.2.1.0
> system-to 14065       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> system-to 14065       root    0u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> system-to 14065       root    1u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> system-to 14065       root    2u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> xfs       15149       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> xfs       15149       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> xfs       15149       root  txt       REG        8,1    89592     253158
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/bin/xfs
> xfs       15149       root  mem       REG        8,1    24252     229064
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libfonte
> nc.so.1.0.0
> xfs       15149       root  mem       REG        8,1   149328      36015
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libm-2.7.so
> xfs       15149       root  mem       REG        8,1    82840      36491
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libz.so
> 1.2.3.3
> xfs       15149       root  mem       REG        8,1   446860     228545
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libfreet
> ype.so.6.3.16
> xfs       15149       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> xfs       15149       root  mem       REG        8,1   381756     229128
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libXfont
> so.1.4.1
> xfs       15149       root  mem       REG        8,1    44068     229229
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/libFS.so
> 6.0.0
> xfs       15149       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> xfs       15149       root    0u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> xfs       15149       root    1u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> xfs       15149       root    2u      CHR        1,3               35380
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/dev/null
> su        15484       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> su        15484       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> su        15484       root  txt       REG        8,1    23748      57206
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/bin/su
> su        15484       root  mem       REG        8,1    44588      35957
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/security/pam
> _unix.so
> su        15484       root  mem       REG        8,1    91852      36172
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libselinux.s
> o.1
> su        15484       root  mem       REG        8,1    38412      36091
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_files
> -2.7.so
> su        15484       root  mem       REG        8,1    34352      36098
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_nis-2
> 7.so
> su        15484       root  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> su        15484       root  mem       REG        8,1    26340      35919
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_compa
> t-2.7.so
> su        15484       root  mem       REG        8,1     7580      35963
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/security/pam
> _mail.so
> su        15484       root  mem       REG        8,1    11228      35961
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/security/pam
> _env.so
> su        15484       root  mem       REG        8,1     3192      35972
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/security/pam
> _rootok.so
> su        15484       root  mem       REG        8,1   254076     180659
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_CTYPE
> su        15484       root  mem       REG        8,1       54     180660
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_NUMERIC
> su        15484       root  mem       REG        8,1     2451     180752
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_TIME
> su        15484       root  mem       REG        8,1   921214     180662
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_COLLATE
> su        15484       root  mem       REG        8,1      286     180753
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_MONETARY
> su        15484       root  mem       REG        8,1       52     180665
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
> su        15484       root  mem       REG        8,1       34     180686
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_PAPER
> su        15484       root  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> su        15484       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> su        15484       root  mem       REG        8,1     8152      36163
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpam_misc
> so.0.81.2
> su        15484       root  mem       REG        8,1    36068      36111
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libpam.so.0
> 81.6
> su        15484       root  mem       REG        8,1    38304      36036
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libcrypt-2.7
> so
> su        15484       root  mem       REG        8,1       77     180703
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_NAME
> su        15484       root  mem       REG        8,1      155     180755
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_ADDRESS
> su        15484       root  mem       REG        8,1       59     180756
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_TELEPHONE
> su        15484       root  mem       REG        8,1       23     180757
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_MEASUREMENT
> su        15484       root  mem       REG        8,1    25700      36349
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/gconv/gc
> onv-modules.cache
> su        15484       root  mem       REG        8,1      373     180758
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_IDENTIFICATION
> su        15484       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> bash      15486       root  cwd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> bash      15486       root  rtd       DIR        8,1     4096      35315
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> bash      15486       root  txt       REG        8,1   675984      57283
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/bin/bash
> bash      15486       root  mem       REG        8,1    38412      36091
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_files
> -2.7.so
> bash      15486       root  mem       REG        8,1    34352      36098
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_nis-2
> 7.so
> bash      15486       root  mem       REG        8,1    75516      35982
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnsl-2.7.s
> o
> bash      15486       root  mem       REG        8,1    26340      35919
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libnss_compa
> t-2.7.so
> bash      15486       root  mem       REG        8,1   254076     180659
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_CTYPE
> bash      15486       root  mem       REG        8,1       54     180660
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_NUMERIC
> bash      15486       root  mem       REG        8,1     2451     180752
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_TIME
> bash      15486       root  mem       REG        8,1   921214     180662
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_COLLATE
> bash      15486       root  mem       REG        8,1      286     180753
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_MONETARY
> bash      15486       root  mem       REG        8,1       52     180665
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
> bash      15486       root  mem       REG        8,1       34     180686
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_PAPER
> bash      15486       root  mem       REG        8,1  1339812      36042
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libc-2.7.so
> bash      15486       root  mem       REG        8,1     9684      36030
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libdl-2.7.so
> bash      15486       root  mem       REG        8,1   185112      35989
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/libncurses.s
> o.5.6
> bash      15486       root  mem       REG        8,1       77     180703
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_NAME
> bash      15486       root  mem       REG        8,1      155     180755
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_ADDRESS
> bash      15486       root  mem       REG        8,1       59     180756
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_TELEPHONE
> bash      15486       root  mem       REG        8,1       23     180757
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_MEASUREMENT
> bash      15486       root  mem       REG        8,1    25700      36349
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/gconv/gc
> onv-modules.cache
> bash      15486       root  mem       REG        8,1      373     180758
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/usr/lib/locale/e
> n_US.utf8/LC_IDENTIFICATION
> bash      15486       root  mem       REG        8,1   117344      36108
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs/lib/ld-2.7.so
> Failed to umount target:
> /var/www/htdocs/moblin-image-creator/asdf6/targets/asdf6/fs
> Traceback (most recent call last):
>   File "/usr/share/pdk/lib/gui.py", line 927, in on_liveCD_clicked
>     self.current_project().create_live_iso(target.name, img_name)
>   File "/usr/share/pdk/lib/Project.py", line 366, in create_live_iso
>     self.umountTarget(target)
>   File "/usr/share/pdk/lib/Project.py", line 362, in umountTarget
>     raise pdk_utils.ImageCreatorUmountError, directory_set
> ImageCreatorUmountError
>  
>
> Any ideas here?
>
>
> On 9/1/08 6:18 PM, "Mitsutaka Amano" <mamano@miraclelinux.com> wrote:
>
>   
>> Hi,
>>
>> Perhaps, You didn't install genisoimage package.
>> Could you install it on host?
>>
>> $ sudo apt-get install genisoimage
>>
>> And it doesn't show error message.
>> As you feel, I'll modify some approach.
>>
>> Regards,
>>
>> ========================================
>>   Mitsutaka Amano

>>   MIRACLE LINUX CORPORATION
>> ========================================
>>
>>
>>
>> MDS wrote:
>>     
>>> Hello All,
>>> I tried exporting my image to a cd, but it crashed the image creator
>>> application and threw the following error:
>>> Any help is appreciated:
>>>
>>> xwd    1:1.0.1-0ubuntu2
>>> xwininfo    1:1.0.2-0ubuntu1
>>> xwud    1:1.0.1-0ubuntu2
>>> zlib1g    1:1.2.3.3.dfsg-5ubuntu2
>>> zlib1g-dev    1:1.2.3.3.dfsg-5ubuntu2
>>> Executing the mksquashfs program: mksquashfs /targets/asusee/fs
>>> /targets/asusee/image/rootfs.img -no-progress -ef
>>> /usr/share/pdk/platforms/mccaslin-lpia/exclude
>>> Parallel mksquashfs: Using 1 processor
>>> Creating little endian 3.0 filesystem on /targets/asusee/image/rootfs.img,
>>> block size 65536.
>>>
>>> Exportable Little endian filesystem, data block size 65536, compressed data,
>>> compressed metadata, compressed fragments, duplicates are removed
>>> Filesystem size 283649.92 Kbytes (277.00 Mbytes)
>>>     40.31% of uncompressed filesystem size (703598.80 Kbytes)
>>> Inode table size 391389 bytes (382.22 Kbytes)
>>>     31.25% of uncompressed inode table size (1252269 bytes)
>>> Directory table size 367913 bytes (359.29 Kbytes)
>>>     50.20% of uncompressed directory table size (732844 bytes)
>>> Number of duplicate files found 1603
>>> Number of inodes 37217
>>> Number of files 28813
>>> Number of fragments 3108
>>> Number of symbolic links  5245
>>> Number of device nodes 88
>>> Number of fifo nodes 2
>>> Number of socket nodes 0
>>> Number of directories 3069
>>> Number of uids 6
>>>     root (0)
>>>     syslog (101)
>>>     unknown (1000)
>>>     man (6)
>>>     news (9)
>>>     klog (102)
>>> Number of gids 14
>>>     video (44)
>>>     audio (29)
>>>     tty (5)
>>>     kmem (15)
>>>     disk (6)
>>>     adm (4)
>>>     shadow (42)
>>>     dhcp (101)
>>>     utmp (43)
>>>     staff (50)
>>>     src (40)
>>>     root (0)
>>>     mail (8)
>>>     klog (103)
>>> Traceback (most recent call last):
>>>   File "/usr/share/pdk/lib/gui.py", line 927, in on_liveCD_clicked
>>>     self.current_project().create_live_iso(target.name, img_name)
>>>   File "/usr/share/pdk/lib/Project.py", line 368, in create_live_iso
>>>     image.create_image()
>>>   File "/usr/share/pdk/lib/InstallImage.py", line 477, in create_image
>>>     pdk_utils.copy("/usr/lib/syslinux/isolinux.bin", self.tmp_path, callback 
>>> = self.progress_callback)
>>>   File "/usr/share/pdk/lib/pdk_utils.py", line 398, in copy
>>>     shutil.copy(src, dst)
>>>   File "/usr/lib/python2.5/shutil.py", line 80, in copy
>>>     copyfile(src, dst)
>>>   File "/usr/lib/python2.5/shutil.py", line 46, in copyfile
>>>     fsrc = open(src, 'rb')
>>> IOError: [Errno 2] No such file or directory: 
>>> '/usr/lib/syslinux/isolinux.bin'
>>> image-creator: Fatal IO error 11 (Resource temporarily unavailable) on X 
>>> server :0.0.
>>> Creating CD image file at: 
>>> /var/www/htdocs/moblin-image-creator/moblin-test-image/targets/asusee/image/t
>>> est.iso
>>> genisoimage: Uh oh, I cant find the boot image 'isolinux.bin' !
>>> Error running command: genisoimage -quiet -o 
>>> /var/www/htdocs/moblin-image-creator/moblin-test-image/targets/asusee/image/t
>>> est.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 
>>> -boot-info-table -l -R -r /tmp/pdk-ZOUSAA
>>> Traceback (most recent call last):
>>>   File "/usr/share/pdk/lib/gui.py", line 927, in on_liveCD_clicked
>>>     self.current_project().create_live_iso(target.name, img_name)
>>>   File "/usr/share/pdk/lib/Project.py", line 368, in create_live_iso
>>>     image.create_image()
>>>   File "/usr/share/pdk/lib/InstallImage.py", line 484, in create_image
>>>     raise EnvironmentError, _("Error running command: %s") % cmd_line
>>> EnvironmentError: Error running command: genisoimage -quiet -o 
>>> /var/www/htdocs/moblin-image-creator/moblin-test-image/targets/asusee/image/t
>>> est.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 
>>> -boot-info-table -l -R -r /tmp/pdk-ZOUSAA
>>> image-creator: Fatal IO error 11 (Resource temporarily unavailable) on X 
>>> server :0.0.
>>>
>>>
>>>
>>>
>>>  EMAILING FOR THE GREATER GOOD
>>> Join me
>>> _______________________________________________
>>> dev mailing list
>>> [email]dev@moblin.org[/email]
>>> [https://www.moblin.org/mailman/listinfo/dev](https://www.moblin.org/mailman/listinfo/dev)
>>>
>>>   
>>>       
>
>
>
>

---


---
title: "Kwin crashes during RAID1 syncing"
date: 2011-02-06
forum: Desktop Environments
---

### Post by gnagnibu on 2011-02-06
Hi everybody.
I'm experiencing an annoyng problem: kwin crashes after autologin and still crashes everytime I reboot pc or restart kdm.
The only different thing after last boot is that /dev/md1 is syncing disks (RAID1)
I'm running kubuntu 10.10 with 2.6.35-24-generic kernel, kde packages 4.5.1
/var/log/kdm.log says:

```

(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
2: /lib/libpthread.so.0 (0x7fa4a0851000+0xfb40) [0x7fa4a0860b40]
3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fa49b1c9000+0xc8e27) [0x7fa49b291e27]
4: /usr/lib/xorg/modules/libwfb.so (wfbBlt+0x136) [0x7fa49ad8f766]
5: /usr/lib/xorg/modules/libwfb.so (wfbCopyNtoN+0x2bf) [0x7fa49ad9421f]
6: /usr/bin/X (miCopyRegion+0xa5) [0x55c2a5]
7: /usr/bin/X (miDoCopy+0x43a) [0x55c93a]
8: /usr/lib/xorg/modules/libwfb.so (wfbCopyArea+0x4c) [0x7fa49ad9363c]
9: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7fa49b1c9000+0x3e1c49) [0x7fa49b5aac49]
10: /usr/bin/X (0x400000+0xdf664) [0x4df664]
11: /usr/bin/X (0x400000+0x3e599) [0x43e599]
12: /usr/bin/X (0x400000+0x3f979) [0x43f979]
13: /usr/bin/X (0x400000+0x2187b) [0x42187b]
14: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fa49f7bcd8e]
15: /usr/bin/X (0x400000+0x21409) [0x421409]
Segmentation fault at address 0x3235c

Caught signal 11 (Segmentation fault). Server aborting
...

```

Any ideas?

Thanks, bye!

---

### Post by dabl on 2011-02-06
Just a guess -- try turning off desktop effects (if you can run systemsettings long enough).

If you do a console login, then

```
sudo service kdm start
```

should start the greeter, and let you log in to X.

If kwin crashes, but you're still in X, then the command is ```
kwin -replace
``` to attempt a restart of kwin.

---

### Post by gnagnibu on 2011-02-08
It's not a RAID problem.
I've tried to reinstall nvidia drivers and I've upgraded kde from 4.5.1 to 4.6 with ppa kubuntu backports:

```

sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade

```but nothing changed.

The goal was:

```

service kdm stop
mv ~/.kde ~/.kde.bak
service kdm start

```I have not yet understood what causes kwin crashes, maybe a new style I've installed days ago...

---

### Post by wizard10000 on 2011-02-08
Got a solution that doesn't solve the problem  :D

I pitched kwin for compiz for several reasons - I think compiz is more stable, more configurable and has a smaller memory footprint than kwin - plus I get to use my favorite emerald theme.

Just for grins why not try installing compiz and you can switch back and forth between the two if need be with fusion-icon.

I'd install 

compiz
compiz-fusion-plugins-extra
compiz-kde
compizconfig-settings-manager
emerald
fusion-icon

Good luck!

---

### Post by gnagnibu on 2011-02-10
Also your solution doesn't solve the problem :D
Maybe, it was a kwin bug, so I think the only way to really solve the problem is patching kwin, isn't it?
But, at the moment, following my way I can use my Desktop, and I think to keep kwin.

Thanks to all.

---


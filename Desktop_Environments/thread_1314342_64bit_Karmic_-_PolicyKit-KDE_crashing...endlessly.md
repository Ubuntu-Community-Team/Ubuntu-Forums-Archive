---
title: "64bit Karmic - PolicyKit-KDE crashing...endlessly"
date: 2009-11-04
forum: Desktop Environments
---

### Post by corck on 2009-11-04
Hi,
I experience the same as already mentioned in this thread
[http://ubuntuforums.org/showthread.php?t=1302024](http://ubuntuforums.org/showthread.php?t=1302024)

every 5 minutes two popups show up PolicyKit-KDE with two identical crash reports. 
Overnight it resulted in 190 such reports.
It happens since my last update a few days ago.
```

Application: PolicyKit-KDE (polkit-kde-manager), signal: Aborted
[KCrash Handler]
#5  0x00007f9f7265a4b5 in *__GI_raise (sig=<value optimized out>) at ../nptl/sysdeps/unix/sysv/linux/raise.c:64
#6  0x00007f9f7265df50 in *__GI_abort () at abort.c:92
#7  0x00007f9f72692c97 in __libc_message (do_abort=<value optimized out>, fmt=<value optimized out>) at ../sysdeps/unix/sysv/linux/libc_fatal.c:189
#8  0x00007f9f7269cdd6 in malloc_printerr (action=3, str=0x7f9f7275e6a8 "double free or corruption (fasttop)", ptr=<value optimized out>) at malloc.c:6217
#9  0x00007f9f726a170c in *__GI___libc_free (mem=<value optimized out>) at malloc.c:3716
#10 0x00007f9f74398056 in PolkitQt::Context::Private::init() () from /usr/lib/libpolkit-qt-core.so.0
#11 0x00007f9f74399b2d in PolkitQt::Context::hasError() const () from /usr/lib/libpolkit-qt-core.so.0
#12 0x000000000040ffce in _start ()

```

I removed policykit-1 policykit-1-gnome to try to stop it, however didn't help.

any ideas would be appreciated

---

### Post by arczi on 2009-11-05
I've got the exact same problem. Kubuntu 9.10, 64 bit. Please post if you find a solution.

---

### Post by BombDiggity on 2009-11-20
Think I might have found a solution

sudo apt-get remove kpackagekit

then 

sudo apt-get install kpackagekit

then

polkit-auth --obtain org.freedesktop.packagekit.system-update

(install anything if it tells you to)

reboot

You should be prompted for a system update, update, it will ask for password (finally)

install updates, enjoy not crashing!

---


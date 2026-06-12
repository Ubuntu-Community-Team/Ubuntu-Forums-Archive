---
title: "gnome-screensaver can't start in fully updated hardy"
date: 2008-06-03
forum: Desktop Environments
---

### Post by xiphosurus on 2008-06-03
gnome-screensaver suddenly stopped working! i have tried complete removal and reinstallation via synaptics package manager and it still fails to load. when i click on the lock screen button, i get the following message.

```
** Message: Screensaver is not running!
```

so i try to load it, and this is wat i get.

```
jkuang@lomega:~$ gnome-screensaver --debug

** (gnome-screensaver:6651): WARNING **: Error retrieving configuration key '/apps/gnome-screensaver/cycle_delay': Type mismatch: Expected `int' got `float' for key /apps/gnome-screensaver/cycle_delay

(gnome-screensaver:6651): GConf-CRITICAL **: gconf_client_get_string: assertion `err == NULL || *err == NULL' failed

** (gnome-screensaver:6651): WARNING **: Error retrieving configuration key '/apps/gnome-screensaver/mode': Type mismatch: Expected \x88
*** glibc detected *** gnome-screensaver: double free or corruption (!prev): 0x0809ac58 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7588a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb758c4f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb77cc8b1]
/usr/lib/libglib-2.0.so.0(g_error_free+0x29)[0xb77b5a79]
gnome-screensaver[0x805df98]
gnome-screensaver[0x805e1a4]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x456)[0xb78aef46]
/usr/lib/libgobject-2.0.so.0[0xb7894242]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x318)[0xb7894a08]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x281)[0xb7895551]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb78956c0]
gnome-screensaver(gs_prefs_new+0x1c)[0x805dacc]
gnome-screensaver[0x8050f56]
/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x456)[0xb78aef46]
/usr/lib/libgobject-2.0.so.0[0xb7894242]
/usr/lib/libgobject-2.0.so.0(g_object_newv+0x318)[0xb7894a08]
/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x281)[0xb7895551]
/usr/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb78956c0]
gnome-screensaver(gs_monitor_new+0x1c)[0x805034c]
gnome-screensaver(main+0xe2)[0x80500c2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7533450]
gnome-screensaver[0x804ff71]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:06 854645     /usr/bin/gnome-screensaver
08068000-08069000 rw-p 00020000 08:06 854645     /usr/bin/gnome-screensaver
08069000-080ab000 rw-p 08069000 00:00 0          [heap]
b7000000-b7021000 rw-p b7000000 00:00 0 
b7021000-b7100000 ---p b7021000 00:00 0 
b7108000-b7111000 r-xp 00000000 08:06 853323     /lib/tls/i686/cmov/libnss_files-2.7.so
b7111000-b7113000 rw-p 00008000 08:06 853323     /lib/tls/i686/cmov/libnss_files-2.7.so
b7113000-b711b000 r-xp 00000000 08:06 853327     /lib/tls/i686/cmov/libnss_nis-2.7.so
b711b000-b711d000 rw-p 00007000 08:06 853327     /lib/tls/i686/cmov/libnss_nis-2.7.so
b711d000-b7124000 r-xp 00000000 08:06 853319     /lib/tls/i686/cmov/libnss_compat-2.7.so
b7124000-b7126000 rw-p 00006000 08:06 853319     /lib/tls/i686/cmov/libnss_compat-2.7.so
b7136000-b7137000 rw-p b7136000 00:00 0 
b7137000-b7176000 r--p 00000000 08:06 885743     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7176000-b7257000 r--p 00000000 08:06 885742     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7257000-b725a000 rw-p b7257000 00:00 0 
b725a000-b725e000 r-xp 00000000 08:06 854696     /usr/lib/libXdmcp.so.6.0.0
b725e000-b725f000 rw-p 00003000 08:06 854696     /usr/lib/libXdmcp.so.6.0.0
b725f000-b7260000 rw-p b725f000 00:00 0 
b7260000-b7277000 r-xp 00000000 08:06 855526     /usr/lib/libxcb.so.1.0.0
b7277000-b7278000 rw-p 00016000 08:06 855526     /usr/lib/libxcb.so.1.0.0
b7278000-b7279000 r-xp 00000000 08:06 855524     /usr/lib/libxcb-xlib.so.0.0.0
b7279000-b727a000 rw-p 00000000 08:06 855524     /usr/lib/libxcb-xlib.so.0.0.0
b727a000-b727c000 r-xp 00000000 08:06 854685     /usr/lib/libXau.so.6.0.0
b727c000-b727d000 rw-p 00001000 08:06 854685     /usr/lib/libXau.so.6.0.0
b727d000-b72a3000 r-xp 00000000 08:06 855344     /usr/lib/libpcre.so.3.12.1
b72a3000-b72a4000 rw-p 00026000 08:06 855344     /usr/lib/libpcre.so.3.12.1
b72a4000-b7303000 r-xp 00000000 08:06 853522     /usr/lib/libgio-2.0.so.0.0.0
b7303000-b7305000 rw-p 0005e000 08:06 853522     /usr/lib/libgio-2.0.so.0.0.0
b7305000-b7306000 rw-p b7305000 00:00 0 
b7306000-b731a000 r-xp 00000000 08:06 853332     /lib/tls/i686/cmov/libpthread-2.7.so
b731a000-b731c000 rw-p 00013000 08:06 853332     /lib/tls/i686/cmov/libpthread-2.7.so
b731c000-b731e000 rw-p b731c000 00:00 0 
b731e000-b7325000 r-Aborted

```

i am running hardy 32bit on 2 computers. BOTH of them can't load gnome-screensaver. gnome-screensaver is version 2.22.2-0ubuntu1.

all repos enabled, so all proposed updates installed. i was thinking maybe one of the proposed updates broke one of the dependencies of gnome-screensaver?

anyone else experiencing this? thanks.

---

### Post by birdy on 2009-04-15
I have the same problem on my Jaunty installation, but my screensaver wasn't working before I upgraded from Hardy either. Did you ever find a solution to this problem? I have messed about using xscreensaver instead of gnome-screensaver, and I'm wondering if that has broken something.

---

### Post by lorebett on 2009-04-15
> **birdy said:**
> I have the same problem on my Jaunty installation, but my screensaver wasn't working before I upgraded from Hardy either. Did you ever find a solution to this problem? I have messed about using xscreensaver instead of gnome-screensaver, and I'm wondering if that has broken something.

same here on Jaunty Beta (brand new installation).
Actually I get:

```
gnome-screensaver

** (gnome-screensaver:9212): WARNING **: screensaver already running in this session

```

but the screensaver never starts (I'm only set to "away")

---

### Post by birdy on 2009-04-15
> **lorebett said:**
> same here on Jaunty Beta (brand new installation).
Actually I get:

```
gnome-screensaver

** (gnome-screensaver:9212): WARNING **: screensaver already running in this session

```



I'm not sure what you mean by "same here" as your screensaver process appears to be up and running. 

In any case I'm not sure gnome-screensaver is supposed to be run by regular users. "sudo gnome-screensaver" works. Not sure why gnome-screensaver doesn't start for me at boot though. I have 

/apps/gnome_settings_daemon/screensaver/start_screensaver

set to true.

---

### Post by lorebett on 2009-04-16
I meant that the screensaver was not starting although it was set...

actually after a log off/logon it seems to work now...

---


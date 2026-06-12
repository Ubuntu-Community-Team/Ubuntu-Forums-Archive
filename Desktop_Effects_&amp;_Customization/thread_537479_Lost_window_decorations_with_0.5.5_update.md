---
title: "Lost window decorations with 0.5.5 update"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by michael37 on 2007-08-28
I had compiz fusion 0.5.2 from Trevino repositories running fine.  I just updated to version 0.5.5 and my window decorations are gone.

Neither gtk-window-decorator nor emerald is working for me now.

Also, here is compiz core dump (btw, where did it put this core dump?)

```

(process:10196): GConf-CRITICAL **: gconf_entry_unref: assertion `REAL_ENTRY (entry)->refcount > 0' failed

(process:10196): GConf-CRITICAL **: ltable_notify: assertion `*key == '/'' failed
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (out): 0x0000000000891700 ***
======= Backtrace: =========
/lib/libc.so.6[0x2adf6c50eb23]
/lib/libc.so.6(cfree+0x8c)[0x2adf6c51226c]
/usr/lib/libgconf-2.so.4(gconf_entry_unref+0x28)[0x2adf70416ca8]
/usr/lib/libgconf-2.so.4[0x2adf7041ef5a]
/usr/lib/libgconf-2.so.4[0x2adf7041f012]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1b4)[0x2adf70f22a14]
/usr/lib/compiz/libglib.so[0x2adf71bcecf8]
/usr/lib/compiz/libglib.so[0x2adf71bcef84]
/usr/bin/compiz.real[0x40e22a]
/usr/bin/compiz.real(eventLoop+0x956)[0x4102f6]
/usr/bin/compiz.real(main+0x436)[0x40c796]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2adf6c4bc8e4]
/usr/bin/compiz.real[0x40bd89]
======= Memory map: ========
00400000-00437000 r-xp 00000000 08:05 458964                             /usr/bin/compiz.real
00637000-00638000 rw-p 00037000 08:05 458964                             /usr/bin/compiz.real
00638000-009f6000 rw-p 00638000 00:00 0                                  [heap]
2adf6a6a7000-2adf6a6c3000 r-xp 00000000 08:05 229391                     /lib/ld-2.5.so
2adf6a6c3000-2adf6a6c6000 rw-p 2adf6a6c3000 00:00 0 
2adf6a8c2000-2adf6a8c4000 rw-p 0001b000 08:05 229391                     /lib/ld-2.5.so
2adf6a8c4000-2adf6a937000 r-xp 00000000 08:05 3935627                    /usr/lib/fglrx/libGL.so.1.2.xlibmesa
2adf6a937000-2adf6ab37000 ---p 00073000 08:05 3935627                    /usr/lib/fglrx/libGL.so.1.2.xlibmesa
2adf6ab37000-2adf6ab41000 rw-p 00073000 08:05 3935627                    /usr/lib/fglrx/libGL.so.1.2.xlibmesa
2adf6ab41000-2adf6ab44000 rw-p 2adf6ab41000 00:00 0 
2adf6ab57000-2adf6ab59000 r-xp 00000000 08:05 3872834                    /usr/lib/libXcomposite.so.1.0.0
2adf6ab59000-2adf6ad58000 ---p 00002000 08:05 3872834                    /usr/lib/libXcomposite.so.1.0.0
2adf6ad58000-2adf6ad59000 rw-p 00001000 08:05 3872834                    /usr/lib/libXcomposite.so.1.0.0
2adf6ad59000-2adf6ad5b000 r-xp 00000000 08:05 3871768                    /usr/lib/libXdamage.so.1.0.0
2adf6ad5b000-2adf6af5a000 ---p 00002000 08:05 3871768                    /usr/lib/libXdamage.so.1.0.0
2adf6af5a000-2adf6af5b000 rw-p 00001000 08:05 3871768                    /usr/lib/libXdamage.so.1.0.0
2adf6af5b000-2adf6af60000 r-xp 00000000 08:05 3870727                    /usr/lib/libXfixes.so.3.1.0
2adf6af60000-2adf6b15f000 ---p 00005000 08:05 3870727                    /usr/lib/libXfixes.so.3.1.0
2adf6b15f000-2adf6b160000 rw-p 00004000 08:05 3870727                    /usr/lib/libXfixes.so.3.1.0
2adf6b160000-2adf6b161000 rw-p 2adf6b160000 00:00 0 
2adf6b161000-2adf6b167000 r-xp 00000000 08:05 3870876                    /usr/lib/libXrandr.so.2.1.0
2adf6b167000-2adf6b367000 ---p 00006000 08:05 3870876                    /usr/lib/libXrandr.so.2.1.0
2adf6b367000-2adf6b368000 rw-p 00006000 08:05 3870876                    /usr/lib/libXrandr.so.2.1.0
2adf6b368000-2adf6b36a000 r-xp 00000000 08:05 3870828                    /usr/lib/libXinerama.so.1.0.0
2adf6b36a000-2adf6b469000 ---p 00002000 08:05 3870828                    /usr/lib/libXinerama.so.1.0.0
2adf6b469000-2adf6b46a000 rw-p 00001000 08:05 3870828                    /usr/lib/libXinerama.so.1.0.0
2adf6b46a000-2adf6b473000 r-xp 00000000 08:05 3870785                    /usr/lib/libSM.so.6.0.0
2adf6b473000-2adf6b673000 ---p 00009000 08:05 3870785                    /usr/lib/libSM.so.6.0.0
2adf6b673000-2adf6b674000 rw-p 00009000 08:05 3870785                    /usr/lib/libSM.so.6.0.0
2adf6b674000-2adf6b675000 rw-p 2adf6b674000 00:00 0 
2adf6b675000-2adf6b68c000 r-xp 00000000 08:05 3870783                    /usr/lib/libICE.so.6.3.0
2adf6b68c000-2adf6b88b000 ---p 00017000 08:05 3870783                    /usr/lib/libICE.so.6.3.0
2adf6b88b000-2adf6b88d000 rw-p 00016000 08:05 3870783                    /usr/lib/libICE.so.6.3.0
2adf6b88d000-2adf6b890000 rw-p 2adf6b88d000 00:00 0 
2adf6b890000-2adf6b8c6000 r-xp 00000000 08:05 3871473                    /usr/lib/libxslt.so.1.1.20
2adf6b8c6000-2adf6bac5000 ---p 00036000 08:05 3871473                    /usr/lib/libxslt.so.1.1.20
2adf6bac5000-2adf6bac7000 rw-p 00035000 08:05 3871473                    /usr/lib//usr/bin/compiz: line 781: 10196 Aborted                 (core dumped) $*

```

---

### Post by michael37 on 2007-08-29
Just fixed Compiz Fusion.  Version 0.5.5 is running fine.

The trick was a complete reinstall (took me a while to reconfigure all my customized options).  My take is some old options are INCOMPATIBLE with new compiz fusion.  I am using standard gtk-window-decorator.

More details [about complete uninstall here](http://ubuntuforums.org/showthread.php?t=533201).

---


---
title: "Problem Installing Kiba-Dock on Gutsy"
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by bevege on 2008-02-25
I'm getting the following error when using this[COLOR="Red"] [Guide ]("(http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba-dock+howto)")[/COLOR]  to install Kiba-dock on Gutsy.  I used the same guide to install kiba-dock on another machine and didn't have any problems.

Any help would be appreciated.

"Kiba was build without Akamaru support Akamaru support"

Here is a copy of the output when I run kiba-dock --verbose

kiba-dock --verbose
Info Message (main.c @ line 161):
        Kiba was build without Akamaru support

Info Message (main.c @ line 164):
        Kiba was build with SVG support

Info Message (main.c @ line 171):
        Kiba was build without GLITZ support

Info Message (main.c @ line 183):
        Kiba was build without SDL support

Misc Message (main.c @ line 257):
        Initiall RSVG Library

Warning (prefs.c @ line 910):
        Invalid Option 'separator_list' added to preferences database!
Warning (prefs.c @ line 910):
        Invalid Option 'dock_groups' added to preferences database!
Warning (prefs.c @ line 910):
        Invalid Option 'dock_position_stepsize' added to preferences database!
Warning (prefs.c @ line 910):
        Invalid Option 'title_disable_on_tasks' added to preferences database!
*** glibc detected *** kiba-dock: double free or corruption (out): 0x080ba1d0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7562d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7566800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7819961]
kiba-dock[0x806ebfa]
kiba-dock(kiba_prefs_add_callback+0xb8)[0x806d608]
kiba-dock(kiba_prefs_callbacks_add+0x182)[0x806e932]
kiba-dock(main+0x3cc)[0x805690c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb750f050]
kiba-dock[0x80564d1]
======= Memory map: ========
08048000-0808a000 r-xp 00000000 08:01 2031622    /usr/local/bin/kiba-dock
0808a000-0808b000 rw-p 00042000 08:01 2031622    /usr/local/bin/kiba-dock
0808b000-08129000 rw-p 0808b000 00:00 0          [heap]
b7100000-b7121000 rw-p b7100000 00:00 0 
b7121000-b7200000 ---p b7121000 00:00 0 
b72d0000-b72da000 r-xp 00000000 08:01 4767787    /lib/libgcc_s.so.1
b72da000-b72db000 rw-p 0000a000 08:01 4767787    /lib/libgcc_s.so.1
b72f0000-b732f000 r--p 00000000 08:01 7716894    /usr/lib/locale/en_US.utf8/LC_CTYPE
b732f000-b7338000 r-xp 00000000 08:01 4341811    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7338000-b733a000 rw-p 00008000 08:01 4341811    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b733a000-b7342000 r-xp 00000000 08:01 4341818    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7342000-b7344000 rw-p 00007000 08:01 4341818    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7344000-b734b000 r-xp 00000000 08:01 4341805    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b734b000-b734d000 rw-p 00006000 08:01 4341805    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b734d000-b7350000 rw-p b734d000 00:00 0 
b7350000-b735f000 r-xp 00000000 08:01 4767833    /lib/libbz2.so.1.0.4
b735f000-b7360000 rw-p 0000f000 08:01 4767833    /lib/libbz2.so.1.0.4
b7360000-b7374000 r-xp 00000000 08:01 4341831    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7374000-b7376000 rw-p 00013000 08:01 4341831    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7376000-b7378000 rw-p b7376000 00:00 0 
b7378000-b73aa000 r-xp 00000000 08:01 7652857    /usr/lib/libcroco-0.6.so.3.0.1
b73aa000-b73ad000 rw-p 00031000 08:01 7652857    /usr/lib/libcroco-0.6.so.3.0.1
b73ad000-b73dd000 r-xp 00000000 08:01 7651494    /usr/lib/libgsf-1.so.114.0.7
b73dd000-b73e0000 rw-p 0002f000 08:01 7651494    /usr/lib/libgsf-1.so.114.0.7
b73e0000-b73e2000 rw-p b73e0000 00:00 0 
b73e2000-b73f6000 r-xp 00000000 08:01 4341800    /lib/tls/i686/cmov/libnsl-2.6.1.so
b73f6000-b73f8000 rw-p 00013000 08:01 4341800    /lib/tls/i686/cmov/libnsl-2.6.1.so
b73f8000-b73fa000 rw-p b73f8000 00:00 0 
b73fa000-b73fe000 r-xp 00000000 08:01 7651578    /usr/lib/libXdmcp.so.6.0.0
b73fe000-b73ff000 rw-p 00003000 08:01 7651578    /usr/lib/libXdmcp.so.6.0.0
b73ff000-b7421000 r-xp 00000000 08:01 6258849    /usr/lib/libpng12.so.0.15.0
b7421000-b7422000 rw-p 00021000 08:01 6258849    /usr/lib/libpng12.so.0.15.0
b7422000-b7424000 r-xp 00000000 08:01 7651351    /usr/lib/libXau.so.6.0.0
b7424000-b7425000 rw-p 00001000 08:01 7651351    /usr/lib/libXau.so.6.0.0
b7425000-b7443000 r-xp 00000000 08:01 6258724    /usr/lib/libexpat.so.1.0.0
b7443000-b7445000 rw-p 0001e000 08:01 6258724    /usr/lib/libexpat.so.1.0.0
b7445000-b7446000 rw-p b7445000 00:00 0 
b7446000-b745a000 r-xp 00000000 08:01 6258728    /usr/lib/libz.so.1.2.3.3
b745a000-b745b000 rw-p 00013000 08:01 6258728    /usr/lib/libz.so.1.2.3.3
b745b000-b74c7000 r-xp 00000000 08:01 6258734    /usr/lib/libfreetype.so.6.3.16
b74c7000-b74cb000 rw-p 0006b000 08:01 6258734    /usr/lib/libfreetype.so.6.3.16
b74cb000-b74f8000 r-xp 00000000 08:01 7651966    /usr/lib/libpangoft2-1.0.so.0.1800.3
b74f8000-b74f9000 rw-p 0002c000 08:01 7651966    /usr/lib/libpangAborted (core dumped)

---

### Post by ronb94 on 2008-02-25
Kiba is not working now, not on the 64bit and not on the 32bit.

---

### Post by bevege on 2008-02-28
Thanks for the reply.  Why does it work on my other machine?  Although, I think I installed it on my other machine before I upgraded to 7.10 but I don't remember.

Thanks,

I'll let it go for now.

---

### Post by ronb94 on 2008-02-28
It worked before.I had kiba-dock running until I reinstalled Gusty and tried to install kiba-dock.

---


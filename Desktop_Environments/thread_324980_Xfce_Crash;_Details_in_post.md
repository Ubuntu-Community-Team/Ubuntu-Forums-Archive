---
title: "Xfce Crash; Details in post"
date: 2006-12-24
forum: Desktop Environments
---

### Post by Clifton396 on 2006-12-24
Hi, I recently installed Ubuntu as well as the Desktops Kubuntu and Xubuntu.
They worked flawlessly for approximately a day but now whenever I change 
the session from KDE or GNOME to Xfce it gives me an error saying Xfce crashed
in less than 10 seconds

The error dialog is as follows:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "clifton"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
libGL warning: 3D driver claims to not support visual 0x4b

(xfwm4:5825): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:5825): libxfcegui4-WARNING **: Disconnected from session manager.
Segmentation fault (core dumped)

I have tried reinstalling xubuntu-desktop but that didn't fix the error.

If anyone can help fix this problem it would be much appreciated,

Clifton

---

### Post by taurus on 2006-12-24
What if you pick Xfce4 in the Sessions at the GUI login screen?  Can you log into XFce4 that way?

---

### Post by Clifton396 on 2006-12-24
That's where I'm launching it from; i.e (options> change session> xfce) under GDM.

---

### Post by Clifton396 on 2006-12-25
*bump*

---

### Post by Clifton396 on 2006-12-25
Alas, I've tried fully reinstalling Xubuntu, xorg-core, x-server, all of the xlibs, zlibcomposite1 as well as the libgl from the error to no avail... I'm really running out of things to reinstall

---

### Post by Clifton396 on 2006-12-25
Well it appears I've made it worse (longer error message anyhow)
See if you can make heads or tails of it...

~/.xsession-errors

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "clifton"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0
libGL warning: 3D driver claims to not support visual 0x4b
*** glibc detected *** /usr/bin/xfce4-session: malloc(): memory corruption: 0x0809af88 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76b11cd]
/lib/tls/i686/cmov/libc.so.6[0xb76b2115]
/lib/tls/i686/cmov/libc.so.6(__libc_realloc+0xff)[0xb76b2cdf]
/usr/lib/libglib-2.0.so.0(g_realloc+0x3b)[0xb77c4bab]
/usr/lib/libglib-2.0.so.0[0xb77d90dc]
/usr/lib/libglib-2.0.so.0(g_string_insert_c+0x3d)[0xb77d93cd]
/usr/lib/libglib-2.0.so.0(g_shell_parse_argv+0x427)[0xb77d3487]
/usr/lib/libxfcegui4.so.4[0xb7f79160]
/usr/lib/libxfcegui4.so.4(xfce_exec+0x2a)[0xb7f798ba]
/usr/bin/xfce4-session[0x8057aa9]
/usr/bin/xfce4-session[0x8054978]
/usr/bin/xfce4-session[0x8054e64]
/usr/bin/xfce4-session[0x8051337]
/usr/lib/libSM.so.6(_SmsProcessMessage+0xc35)[0xb7fac315]
/usr/lib/libICE.so.6(IceProcessMessages+0x308)[0xb7fa040e]
/usr/bin/xfce4-session[0x804f2d2]
/usr/lib/libglib-2.0.so.0[0xb77e6c8d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb77bd802]
/usr/lib/libglib-2.0.so.0[0xb77c07df]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb77c0b89]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7d28574]
/usr/bin/xfce4-session[0x804f74c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb765f8cc]
/usr/bin/xfce4-session[0x804ec41]
======= Memory map: ========
08048000-0805c000 r-xp 00000000 03:02 1629071    /usr/bin/xfce4-session
0805c000-0805d000 rw-p 00014000 03:02 1629071    /usr/bin/xfce4-session
0805d000-0809e000 rw-p 0805d000 00:00 0          [heap]
b7200000-b7221000 rw-p b7200000 00:00 0 
b7221000-b7300000 ---p b7221000 00:00 0 
b73de000-b73f0000 r-xp 00000000 03:02 785921     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b73f0000-b73f1000 rw-p 00011000 03:02 785921     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b73f1000-b73fa000 r-xp 00000000 03:02 1257274    /lib/tls/i686/cmov/libnss_files-2.4.so
b73fa000-b73fc000 rw-p 00008000 03:02 1257274    /lib/tls/i686/cmov/libnss_files-2.4.so
b73fc000-b7404000 r-xp 00000000 03:02 1257278    /lib/tls/i686/cmov/libnss_nis-2.4.so
b7404000-b7406000 rw-p 00007000 03:02 1257278    /lib/tls/i686/cmov/libnss_nis-2.4.so
b7406000-b740d000 r-xp 00000000 03:02 1257270    /lib/tls/i686/cmov/libnss_compat-2.4.so
b740d000-b740f000 rw-p 00006000 03:02 1257270    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7412000-b741c000 r-xp 00000000 03:02 1254243    /lib/libgcc_s.so.1
b741c000-b741d000 rw-p 00009000 03:02 1254243    /lib/libgcc_s.so.1
b741d000-b741e000 r-xp 00000000 03:02 785381     /usr/lib/gconv/ISO8859-1.so
b741e000-b7420000 rw-p 00001000 03:02 785381     /usr/lib/gconv/ISO8859-1.so
b7420000-b7421000 r-xp 00000000 03:02 784208     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7421000-b7422000 rw-p 00000000 03:02 784208     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7422000-b7455000 r--p 00000000 03:02 848232     /usr/lib/locale/en_US.utf8/LC_CTYPE
b7455000-b752c000 r--p 00000000 03:02 848231     /usr/lib/locale/en_US.utf8/LC_COLLATE
b752c000-b752e000 rw-p b752c000 00:00 0 
b752e000-b7540000 r-xp 00000000 03:02 1257268    /lib/tls/i686/cmov/libnsl-2.4.so
b7540000-b7542000 rw-p 00011000 03:02 1257268    /lib/tls/i686/cmov/libnsl-2.4.so
b7542000-b7544000 rw-p b7542000 00:00 0 
b7544000-b754b000 r-xp 00000000 03:02 1257287    /lib/tls/i686/cmov/librt-2.4.so
b754b000-b754d000 rw-p 00006000 03:02 1257287    /lib/tls/i686/cmov/librt-2.4.so
b754d000-b754e000 rw-p b754d000 00:00 0 
b754e000-b7552000 r-xp 00000000 03:02 783331     /usr/lib/libXdmcp.so.6.0.0
b7552000-b7553000 rw-p 00003000 03:02 783331     /usr/lib/libXdmcp.so.6.0.0
b7553000-b7576000 r-xp 00000000 03:02 783462     /usr/lib/libpng12.so.0.1.2.8
b7576000-b7577000 rw-p 00023000 03:02 783462     /usr/lib/libpng12.so.0.1.2.8
b7577000-b7579000 r-xp 00000000 03:02 783322     /usr/lib/libXau.so.6.0.0
b7579000-b757a000 rw-p 00001000 03:02 783322     /usr/lib/libXau.so.6.0.0
b757a000-b7596000 r-xp 00000000 03:02 783516     /usr/lib/libexpat.so.1.0.0
b7596000-b7598000 rw-p 0001c000 03:02 783516     /usr/lib/libexpat.so.1.0.0
b7598000-b75ab000 r-xp 00000000 03:02 784062     /usr/lib/libz.so.1.2.3
b75ab000-b75ac000 rw-p 00012000 03:02 784062     /usr/lib/libz.so.1.2.3
b75ac000-b75ad000 rw-p b75ac000 00:00 0 
b75ad000-b7614000 r-xp 00000000 03:02 783532     /usr/lib/libfreetype.so.6.3.10
b7614000-b7617000 rw-p 00067000 03:02 783532     /usr/lib/libfreetype.so.6.3.10
b7617000-b7641000 r-xp 00000000 03:02 783907     /usr/lib/libpangoft2-1.0.so.0.1400.5
b7641000-b7642000 rw-p 00029000 03:02 783907     /usr/lib/libpangoft2-1.0.so.0.1400.5
b7642000-b7649000 r-xp 00000000 03:02 784001     /usr/lib/libstartup-notification-1.so.0.0.0
b7649000-b764a000 rw-p 00006000 03:02 784001     /usr/lib/libstartup-notification-1.so.0.0.0
b764a000-b7777000 r-xp 00000000 03:02 1257257    /lib/tls/i686/cmov/libc-2.4.so
b7777000-b7779000 r--p 0012c000 03:02 1257257    /lib/tls/i686/cmov/libc-2.4.so
b7779000-b777b000 rw-p 0012e000 03:02 1257257    /lib/tls/i686/cmov/libc-2.4.so
b777b000-b777f000 rw-p b777b000 00:00 0 
b777f000-b778e000 r-xp 00000000 03:02 1257283    /lib/tls/i686/cmov/libpthread-2.4.so
b778e000-b7790000 rw-p 0000f000 03:02 1257283    /lib/tls/i686/cmov/libpthread-2.4.so
b7790000-b7792000 rw-p b7790000 00:00 0 
b7792000-b7823000 r-xp 00000000 03:02 782243     /usr/lib/libglib-2.0.so.0.1200.4
b7823000-b7824000 rw-p 00091000 03:02 782243     /usr/lib/libglib-2.0.so.0.1200.4
b7824000-b7828000 r-xp 00000000 03:02 1678086    /usr/lib/libgthread-2.0.so.0.1200.4
b7828000-b7829000 rw-p 00003000 03:02 1678086    /usr/lib/libgthread-2.0.so.0.1200.4
b7829000-b782b000 r-xp 00000000 03:02 1257263    /lib/tls/i686/cmov/libdl-2.4.so
b782b000-b782d000 rw-p 00001000 03:02 1257263    /lib/tls/i686/cmov/libdl-2.4.so
b782d000-b7830000 r-xp 00000000 03:02 1677766    /usr/lib/libgmodule-2.0.so.0.1200.4
b7830000-b7831000 rw-p 00002000 03:02 1677766    /usr/lib/libgmodule-2.0.so.0.1200.4
b7831000-b7855000 r-xp 00000000 03:02 1257265    /lib/tls/i686/cmov/libm-2.4.so
b7855000-b7857000 rw-p 00023000 03:02 1257265    /lib/tls/i686/cmov/libm-2.4.so
b7857000-b7858000 rw-p b7857000 00:00 0 
b7858000-b789f000 r-xp 00000000 03:02 783304     /usr/lib/libORBit-2.so.0.1.0
b789f000-b78a9000 rw-p 00046000 03:02 783304     /usr/lib/libORBit-2.so.0.1.0
b78a9000-b78d7000 r-xp 00000000 03:02 783557     /usr/lib/libgconf-2.so.4.1.0
b78d7000-b78da000 rw-p 0002e000 03:02 783557     /usr/lib/libgconf-2.so.4.1.0
b78da000-b7909000 r-xp 00000000 03:02 783456     /usr/lib/libdbus-1.so.3.0.0
b7909000-b790a000 rw-p 0002f000 03:02 783456     /usr/lib/libdbus-1.so.3.0.0
b790a000-b7924000 r-xp 00000000 03:02 783458     /usr/lib/libdbus-glib-1.so.2.0.0
b7924000-b7925000 rw-p 00019000 03:02 783458     /usr/lib/libdbus-glib-1.so.2.0.0
b7925000-b795e000 r-xp 00000000 03:02 1677765    /usr/lib/libgobject-2.0.so.0.1200.4
b795e000-b795f000 rw-p 00038000 03:02 1677765    /usr/lib/libgobject-2.0.so.0.1200.4
b795f000-b7a25000 r-xp 00000000 03:02 783316     /usr/lib/libX11.so.6.2.0
b7a25000-b7a28000 rw-p 000c5000 03:02 783316     /usr/lib/libX11.so.6.2.0
b7a28000-b7a29000 rw-p b7a28000 00:00 0 
b7a29000-b7a89000 r-xp 00000000 03:02 783427     /usr/lib/libcairo.so.2.9.2
b7a89000-b7a8b000 rw-p 0005f000 03:02 783427     /usr/lib/libcairo.so.2.9.2
b7a8b000-b7ac3000 r-xp 00000000 03:02 783903     /usr/lib/libpango-1.0.so.0.1400.5
b7ac3000-b7ac5000 rw-p 00037000 03:02 783903     /usr/lib/libpango-1.0.so.0.1400.5
b7ac5000-b7ac9000 r-xp 00000000 03:02 783337     /usr/lib/libXfixes.so.3.1.0
b7ac9000-b7aca000 rw-p 00003000 03:02 783337     /usr/lib/libXfixes.so.3.1.0
b7aca000-b7ad2000 r-xp 00000000 03:02 783327     /usr/lib/libXcursor.so.1.0.2
b7ad2000-b7ad3000 rw-p 00007000 03:02 783327     /usr/lib/libXcursor.so.1.0.2
b7ad3000-b7ad5000 r-xp 00000000 03:02 783355     /usr/lib/libXrandr.so.2.0.0
b7ad5000-b7ad6000 rw-p 00002000 03:02 783355     /usr/lib/libXrandr.so.2.0.0
b7ad6000-b7add000 r-xp 00000000 03:02 783343     /usr/lib/libXi.so.6.0.0
b7add000-b7ade000 rw-p 00006000 03:02 783343     /usr/lib/libXi.so.6.0.0
b7ade000-b7adf000 rw-p b7ade000 00:00 0 
b7adf000-b7ae1000 r-xp 00000000 03:02 783345     /usr/lib/libXinerama.so.1.0.0
b7ae1000-b7ae2000 rw-p 00001000 03:02 783345     /usr/lib/libXinerama.so.1.0.0
b7ae2000-b7ae9000 r-xp 00000000 03:02 783357     /usr/lib/libXrender.so.1.3.0
b7ae9000-b7aea000 rw-p 00006000 03:02 783357     /usr/lib/libXrender.so.1.3.0
b7aea000-b7af6000 r-xp 00000000 03:02 783335     /usr/lib/libXext.so.6.4.0
b7af6000-b7af7000 rw-p 0000c000 03:02 783335     /usr/lib/libXext.so.6.4.0
b7af7000-b7b20000 r-xp 00000000 03:02 783522     /usr/lib/libfontconfig.so.1.0.4
b7b20000-b7b25000 rw-p 00028000 03:02 783522     /usr/lib/libfontconfig.so.1.0.4
b7b25000-b7b26000 rw-p b7b25000 00:00 0 
b7b26000-b7b2d000 r-xp 00000000 03:02 783905     /usr/lib/libpangocairo-1.0.so.0.1400.5
b7b2d000-b7b2e000 rw-p 00006000 03:02 783905     /usr/lib/libpangocairo-1.0.so.0.1400.5
b7b2e000-b7b43000 r-xp 00000000 03:02 786102     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b7b43000-b7b44000 rw-p 00015000 03:02 786102     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b7b44000-b7b45000 rw-p b7b44000 00:00 0 
b7b45000-b7b5d000 r-xp 00000000 03:02 783394     /usr/lib/libatk-1.0.so.0.1213.0
b7b5d000-b7b5f000 rw-p 00017000 03:02 783394     /usr/lib/libatk-1.0.so.0.1213.0
b7b5f000-b7be0000 r-xp 00000000 03:02 786103     /usr/lib/libgdk-x11-2.0.so.0.1000.6
b7be0000-b7be3000 rw-p 00081000 03:02 786103     /usr/lib/libgdk-x11-2.0.so.0.1000.6
b7be3000-b7bef000 r-xp 00000000 03:02 1678041    /usr/lib/libxfce4util.so.4.0.0
b7bef000-b7bf0000 rw-p 0000b000 03:02 1678041    /usr/lib/libxfce4util.so.4.0.0
b7bf0000-b7bf1000 rw-p b7bf0000 00:00 0 
b7bf1000-b7f3a000 r-xp 00000000 03:02 786790     /usr/lib/libgtk-x11-2.0.so.0.1000.6
b7f3a000-b7f40000 rw-p 00349000 03:02 786790     /usr/lib/libgtk-x11-2.0.so.0.1000.6
b7f40000-b7f41000 rw-p b7f40000 00:00 0 
b7f41000-b7f86000 r-xp 00000000 03:02 1678094    /usr/lib/libxfcegui4.so.4.2.0
b7f86000-b7f88000 rw-p 00045000 03:02 1678094    /usr/lib/libxfcegui4.so.4.2.0
b7f88000-b7f89000 rw-p b7f88000 00:00 0 
b7f89000-b7f8d000 r-xp 00000000 03:02 1678043    /usr/lib/libxfce4mcs-client.so.3.0.1
b7f8d000-b7f8e000 rw-p 00003000 03:02 1678043    /usr/lib/libxfce4mcs-client.so.3.0.1
b7f8e000-b7f8f000 rw-p b7f8e000 00:00 0 
b7f8f000-b7fa4000 r-xp 00000000 03:02 783294     /usr/lib/libICE.so.6.3.0
b7fa4000-b7fa5000 rw-p 00014000 03:02 783294     /usr/lib/libICE.so.6.3.0
b7fa5000-b7fa7000 rw-p b7fa5000 00:00 0 
b7fa7000-b7faf000 r-xp 00000000 03:02 783312     /usr/lib/libSM.so.6.0.0
b7faf000-b7fb0000 rw-p 00007000 03:02 783312     /usr/lib/libSM.so.6.0.0
b7fb0000-b7fb3000 r-xp 00000000 03:02 1678061    /usr/lib/libxfsm-4.2.so.0.0.1
b7fb3000-b7fb4000 rw-p 00002000 03:02 1678061    /usr/lib/libxfsm-4.2.so.0.0.1
b7fb4000-b7fb5000 r--p 00000000 03:02 848237     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7fb5000-b7fb6000 r--p 00000000 03:02 848240     /usr/lib/locale/en_US.utf8/LC_TIME
b7fb6000-b7fb7000 r--p 00000000 03:02 848235     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fb7000-b7fb8000 r--p 00000000 03:02 848241     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fb8000-b7fb9000 r--p 00000000 03:02 848238     /usr/lib/locale/en_US.utf8/LC_PAPER
b7fb9000-b7fba000 r--p 00000000 03:02 848236     /usr/lib/locale/en_US.utf8/LC_NAME
b7fba000-b7fbb000 r--p 00000000 03:02 848230     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fbb000-b7fbc000 r--p 00000000 03:02 848239     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fbc000-b7fbd000 r--p 00000000 03:02 848234     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fbd000-b7fc4000 r--s 00000000 03:02 785433     /usr/lib/gconv/gconv-modules.cache
b7fc4000-b7fc5000 r--p 00000000 03:02 848233     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fc5000-b7fc7000 rw-p b7fc5000 00:00 0 
b7fc7000-b7fe0000 r-xp 00000000 03:02 1254198    /lib/ld-2.4.so
b7fe0000-b7fe2000 rw-p 00018000 03:02 1254198    /lib/ld-2.4.so
bf8ec000-bf901000 rw-p bf8ec000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

(xfwm4:7227): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:7227): libxfcegui4-WARNING **: Disconnected from session manager.
Aborted (core dumped)

---

### Post by elsenator on 2007-03-05
*bump* I'm having this exact same problem. I installed Xubuntu the other day, and today, when i logged out and logged back in, it told me the session lasted less than 10 seconds, and by looking in the xserver error file, i have the exact same error as Clifton.

did anyone run into this problem, and if so, do you know how to fix it?

---

### Post by charding on 2008-06-15
I am getting the same problem with ICEauthority having a segmentation fault. I found this was after the Package Panager in xubuntu auth installed xserver-xorg-core yesterday.

I can't log into xfce any more and gnome works ok. Strange.

---


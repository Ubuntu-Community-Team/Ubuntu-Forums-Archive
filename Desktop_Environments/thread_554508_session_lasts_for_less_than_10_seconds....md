---
title: "session lasts for less than 10 seconds..."
date: 2007-09-19
forum: Desktop Environments
---

### Post by tzramsoy on 2007-09-19
Hi guys,

After installing some ware (conky) and setting it to startup during the session together with a gdesklets hack, my session crashes restarts, and I have to log in again

I have tried the options listed in this forum:
 [here]("http://ubuntuforums.org/showthread.php?t=23467") 
[here]("http://ubuntuforums.org/showthread.php?t=478346") and those suggested at this forum

but it hasn't helped with the crash issue. I have also removed both conky and gdesklets but it hasn't helped.

So here is my error log, after the standard "Your session only lasted less than 10 seconds (...)":

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "thomasr"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/th1:/tmp/.ICE-unix/6070
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Initializing gnome-mount extension

(update-notifier:6164): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6166): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gedit:6171): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6174): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6168): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

In my previous login, a longer error message/report appeared instead:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "thomasr"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/th1:/tmp/.ICE-unix/6076
Initializing gnome-mount extension
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
*** glibc detected *** /usr/bin/gnome-session: malloc(): memory corruption: 0x0000000000a23960 ***
======= Backtrace: =========
/lib/libc.so.6[0x2acc1051b1d1]
/lib/libc.so.6(__libc_malloc+0x7d)[0x2acc1051c98d]
/usr/lib/libglib-2.0.so.0(g_malloc+0x2b)[0x2acc1003690b]
/usr/lib/libglib-2.0.so.0(g_io_channel_unix_new+0x15)[0x2acc10057215]
/usr/bin/gnome-session[0x410068]
/usr/bin/gnome-session(ice_thawed+0x49)[0x4100e9]
/usr/bin/gnome-session[0x410242]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1b4)[0x2acc1002fa14]
/usr/lib/libglib-2.0.so.0[0x2acc1003285d]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2acc10032b6a]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2acc0d95e023]
/usr/bin/gnome-session(main+0x4d4)[0x410d14]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2acc104c88e4]
/usr/bin/gnome-session[0x40caf9]
======= Memory map: ========
00400000-00424000 r-xp 00000000 08:01 13386991                           /usr/bin/gnome-session
00624000-00626000 rw-p 00024000 08:01 13386991                           /usr/bin/gnome-session
00626000-00a58000 rw-p 00626000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rw-p 40001000 00:00 0 
2aaaaaace000-2aaaaaadb000 r-xp 00000000 08:01 10174560                   /lib/libgcc_s.so.1
2aaaaaadb000-2aaaaacdb000 ---p 0000d000 08:01 10174560                   /lib/libgcc_s.so.1
2aaaaacdb000-2aaaaacdc000 rw-p 0000d000 08:01 10174560                   /lib/libgcc_s.so.1
2aaaac000000-2aaaac021000 rw-p 2aaaac000000 00:00 0 
2aaaac021000-2aaab0000000 ---p 2aaaac021000 00:00 0 
2acc0c6fd000-2acc0c719000 r-xp 00000000 08:01 10174506                   /lib/ld-2.5.so
2acc0c719000-2acc0c71c000 rw-p 2acc0c719000 00:00 0 
2acc0c918000-2acc0c91a000 rw-p 0001b000 08:01 10174506                   /lib/ld-2.5.so
2acc0c91a000-2acc0c91c000 r-xp 00000000 08:01 13388007                   /usr/lib/libXau.so.6.0.0
2acc0c91c000-2acc0cb1b000 ---p 00002000 08:01 13388007                   /usr/lib/libXau.so.6.0.0
2acc0cb1b000-2acc0cb1c000 rw-p 00001000 08:01 13388007                   /usr/lib/libXau.so.6.0.0
2acc0cb1c000-2acc0cb26000 r-xp 00000000 08:01 13386501                   /usr/lib/libesd.so.0.2.36
2acc0cb26000-2acc0cd26000 ---p 0000a000 08:01 13386501                   /usr/lib/libesd.so.0.2.36
2acc0cd26000-2acc0cd27000 rw-p 0000a000 08:01 13386501                   /usr/lib/libesd.so.0.2.36
2acc0cd27000-2acc0cd3d000 r-xp 00000000 08:01 13386275                   /usr/lib/libgnome-desktop-2.so.2.3.5
2acc0cd3d000-2acc0cf3d000 ---p 00016000 08:01 13386275                   /usr/lib/libgnome-desktop-2.so.2.3.5
2acc0cf3d000-2acc0cf3e000 rw-p 00016000 08:01 13386275                   /usr/lib/libgnome-desktop-2.so.2.3.5
2acc0cf3e000-2acc0cfd7000 r-xp 00000000 08:01 13386061                   /usr/lib/libgnomeui-2.so.0.1788.4
2acc0cfd7000-2acc0d1d7000 ---p 00099000 08:01 13386061                   /usr/lib/libgnomeui-2.so.0.1788.4
2acc0d1d7000-2acc0d1dd000 rw-p 00099000 08:01 13386061                   /usr/lib/libgnomeui-2.so.0.1788.4
2acc0d1dd000-2acc0d1de000 rw-p 2acc0d1dd000 00:00 0 
2acc0d1de000-2acc0d1e7000 r-xp 00000000 08:01 13388067                   /usr/lib/libSM.so.6.0.0
2acc0d1e7000-2acc0d3e7000 ---p 00009000 08:01 13388067                   /usr/lib/libSM.so.6.0.0
2acc0d3e7000-2acc0d3e8000 rw-p 00009000 08:01 13388067                   /usr/lib/libSM.so.6.0.0
2acc0d3e8000-2acc0d3ff000 r-xp 00000000 08:01 13388065                   /usr/lib/libICE.so.6.3.0
2acc0d3ff000-2acc0d5fe000 ---p 00017000 08:01 13388065                   /usr/lib/libICE.so.6.3.0
2acc0d5fe000-2acc0d600000 rw-p 00016000 08:01 13388065                   /usr/lib/libICE.so.6.3.0
2acc0d600000-2acc0d603000 rw-p 2acc0d600000 00:00 0 
2acc0d603000-2acc0d61a000 r-xp 00000000 08:01 13390355                   /usr/lib/libgnome-2.so.0.1800.0
2acc0d61a000-2acc0d819000 ---p 00017000 08:01 13390355                   /usr/lib/libgnome-2.so.0.1800.0
2acc0d819000-2acc0d81b000 rw-p 00016000 08:01 13390355                   /usr/lib/libgnome-2.so.0.1800.0
2acc0d81b000-2acc0d81c000 rw-p 2acc0d81b000 00:00 0 
2acc0d81c000-2acc0dbab000 r-xp 00000000 08:01 13389535                   /usr/lib/libgtk-x11-2.0.so.0.1000.11
2acc0dbab000-2acc0ddaa000 ---p 0038f000 08:01 13389535                   /usr/lib/libgtk-x11-2.0.so.0.1000.11
2acc0ddaa000-2acc0ddb5000 rw-p 0038e000 08:01 13389535                   /usr/lib/libgtk-x11-2.0.so.0.1000.11
2acc0ddb5000-2acc0ddb7000 rw-p 2acc0ddb5000 00:00 0 
2acc0ddb7000-2acc0de4c000 r-xp 00000000 08:01 13389530                   /usr/lib/libgdk-x11-2.0.so.0.1000.11
2acc0de4c000-2acc0e04b000 ---p 00095000 08:01 13389530                   /usr/lib/libgdk-x11-2.0.so.0.1000.11
2acc0e04b000-2acc0e050000 rw-p 00094000 08:01 13389530                   /usr/lib/libgdk-x11-2.0.so.0.1000.11
2acc0e050000-2acc0e06e000 r-xp 00000000 08:01 13389481                   /usr/lib/libatk-1.0.so.0.1809.1
2acc0e06e000-2acc0e26e000 ---p 0001e000 08:01 13389481                   /usr/lib/libatk-1.0.so.0.1809.1
2acc0e26e000-2acc0e271000 rw-p 0001e000 08:01 13389481                   /usr/lib/libatk-1.0.so.0.1809.1
2acc0e271000-2acc0e272000 rw-p 2acc0e271000 00:00 0 
2acc0e272000-2acc0e289000 r-xp 00000000 08:01 13387446                   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
2acc0e289000-2acc0e489000 ---p 00017000 08:01 13387446                   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
2acc0e489000-2acc0e48a000 rw-p 00017000 08:01 13387446                   /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
2acc0e48a000-2acc0e490000 r-xp 00000000 08:01 13389469                   /usr/lib/libXrandr.so.2.1.0
2acc0e490000-2acc0e690000 ---p 00006000 08:01 13389469                   /usr/lib/libXrandr.so.2.1.0
2acc0e690000-2acc0e691000 rw-p 00006000 08:01 13389469                   /usr/lib/libXrandr.so.2.1.0
2acc0e691000-2acc0e6d3000 r-xp 00000000 08:01 13389508                   /usr/lib/libpango-1.0.so.0.1600.2
2acc0e6d3000-2acc0e8d3000 ---p 00042000 08:01 13389508                   /usr/lib/libpango-1.0.so.0.1600.2
2acc0e8d3000-2acc0e8d6000 rw-p 00042000 08:01 13389508                   /usr/lib/libpango-1.0.so.0.1600.2
2acc0e8d6000-2acc0e8d7000 rw-p 2acc0e8d6000 00:00 0 
2acc0e8d7000-2acc0e9dd000 r-xp 00000000 08:01 13386537                   /usr/lib/libX11.so.6.2.0
2acc0e9dd000-2acc0ebdd000 ---p 00106000 08:01 13386537                   /usr/lib/libX11.so.6.2.0
2acc0ebdd000-2acc0ebe4000 rw-p 00106000 08:01 13386537                   /usr/lib/libX11.so.6.2.0
2acc0ebe4000-2acc0ec49000 r-xp 00000000 08:01 13386541                   /usr/lib/libbonobo-2.so.0.0.0
2acc0ec49000-2acc0ee48000 ---p 00065000 08:01 13386541                   /usr/lib/libbonobo-2.so.0.0.0
2acc0ee48000-2acc0ee59000 rw-p 00064000 08:01 13386541                   /usr/lib/libbonobo-2.so.0.0.0
2acc0ee59000-2acc0ee70000 r-xp 00000000 08:01 13387040                   /usr/lib/libbonobo-activation.so.4.0.0
2acc0ee70000-2acc0f070000 ---p 00017000 08:01 13387040                   /usr/lib/libbonobo-activation.so.4.0.0
2acc0f070000-2acc0f074000 rw-p 00017000 08:01 13387040                   /usr/lib/libbonobo-activation.so.4.0.0
2acc0f074000-2acc0f075000 rw-p 2acc0f074000 00:00 0 
2acc0f075000-2acc0f0ae000 r-xp 00000000 08:01 13386047                   /usr/lib/libgconf-2.so.4.1.2
2acc0f0ae000-2acc0f2ad000 ---p 00039000 08:01 13386047                   /usr/lib/libgconf-2.so.4.1.2
2acc0f2ad000-2acc0f2b2000 rw-p 00038000 08:01 13386047                   /usr/lib/libgconf-2.so.4.1.2
2acc0f2b2000-2acc0f30e000 r-xp 00000000 08:01 13386472                   /usr/lib/libORBit-2.so.0.1.0
2acc0f30e000-2acc0f50d000 ---p 0005c000 08:01 13386472                   /usr/lib/libORBit-2.so.0.1.0
2acc0f50d000-2acc0f520000 rw-p 0005b000 08:01 13386472                   /usr/lib/libORBit-2.so.0.1.0
2acc0f520000-2acc0f521000 r--p 00000000 08:01 13618644                   /usr/lib/locale/en_AU.utf8/LC_IDENTIFICATION
2acc0f521000-2acc0f528000 r--s 00000000 08:01 13402432                   /usr/lib/gconv/gconv-modules.cache
2acc0f528000-2acc0f529000 r--p 00000000 08:01 13615575                   /usr/lib/locale/en_AU.utf8/LC_MEASUREMENT
2acc0f529000-2acc0f52a000 r--p 00000000 08:01 13618643                   /usr/lib/locale/en_AU.utf8/LC_TELEPHONE
2acc0f52a000-2acc0f52b000 r--p 00000000 08:01 13618642                   /usr/lib/locale/en_AU.utf8/LC_ADDRESS
2acc0f52b000-2acc0f52c000 r--p 00000000 08:01 13615572                   /usr/lib/locale/en_AU.utf8/LC_NAME
2acc0f52c000-2acc0f52d000 r--p 00000000 08:01 13615571                   /usr/lib/locale/en_AU.utf8/LC_PAPER
2acc0f52d000-2acc0f52e000 r--p 00000000 08:01 13615570                   /usr/lib/locale/en_AU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2acc0f52e000-2acc0f52f000 r--p 00000000 08:01 13618641                   /usr/lib/locale/en_AU.utf8/LC_MONETARY
2acc0f53b000-2acc0f550000 r-xp 00000000 08:01 10174834                   /lib/libpthread-2.5.so
2acc0f550000-2acc0f750000 ---p 00015000 08:01 10174834                   /lib/libpthread-2.5.so
2acc0f750000-2acc0f752000 rw-p 00015000 08:01 10174834                   /lib/libpthread-2.5.so
2acc0f752000-2acc0f757000 rw-p 2acc0f752000 00:00 0 
2acc0f757000-2acc0f775000 r-xp 00000000 08:01 13387332                   /usr/lib/libdbus-glib-1.so.2.1.0
2acc0f775000-2acc0f975000 ---p 0001e000 08:01 13387332                   /usr/lib/libdbus-glib-1.so.2.1.0
2acc0f975000-2acc0f977000 rw-p 0001e000 08:01 13387332                   /usr/lib/libdbus-glib-1.so.2.1.0
2acc0f977000-2acc0f9ae000 r-xp 00000000 08:01 13388071                   /usr/lib/libdbus-1.so.3.2.0
2acc0f9ae000-2acc0fbad000 ---p 00037000 08:01 13388071                   /usr/lib/libdbus-1.so.3.2.0
2acc0fbad000-2acc0fbaf000 rw-p 00036000 08:01 13388071                   /usr/lib/libdbus-1.so.3.2.0
2acc0fbaf000-2acc0fbef000 r-xp 00000000 08:01 13389475                   /usr/lib/libgobject-2.0.so.0.1200.11
2acc0fbef000-2acc0fdef000 ---p 00040000 08:01 13389475                   /usr/lib/libgobject-2.0.so.0.1200.11
2acc0fdef000-2acc0fdf1000 rw-p 00040000 08:01 13389475                   /usr/lib/libgobject-2.0.so.0.1200.11
2acc0fdf1000-2acc0fdf2000 rw-p 2acc0fdf1000 00:00 0 
2acc0fdf2000-2acc0fe00000 r-xp 00000000 08:01 13387339                   /usr/lib/libgnome-keyring.so.0.0.1
2acc0fe00000-2acc0ffff000 ---p 0000e000 08:01 13387339                   /usr/lib/libgnome-keyring.so.0.0.1
2acc0ffff000-2acc10000000 rw-p 0000d000 08:01 13387339                   /usr/lib/libgnome-keyring.so.0.0.1
2acc10000000-2acc100a0000 r-xp 00000000 08:01 13389474                   /usr/lib/libglib-2.0.so.0.1200.11
2acc100a0000-2acc1029f000 ---p 000a0000 08:01 13389474                   /usr/lib/libglib-2.0.so.0.1200.11
2acc1029f000-2acc102a1000 rw-p 0009f000 08:01 13389474                   /usr/lib/libglib-2.0.so.0.1200.11
2acc102a1000-2acc102a9000 r-xp 00000000 08:01 10174772                   /lib/libwrap.so.0.7.6
2acc102a9000-2acc104a8000 ---p 00008000 08:01 10174772                   /lib/libwrap.so.0.7.6
2acc104a8000-2acc104aa000 rw-p 00007000 08:01 10174772                   /lib/libwrap.so.0.7.6
2acc104aa000-2acc104ab000 rw-p 2acc104aa000 00:00 0 
2acc104ab000-2acc105f2000 r-xp 00000000 08:01 10174818                   /lib/libc-2.5.so
2acc105f2000-2acc107f2000 ---p 00147000 08:01 10174818                   /lib/libc-2.5.so
2acc107f2000-2acc107f5000 r--p 00147000 08:01 10174818                   /lib/libc-2.5.so
2acc107f5000-2acc107f7000 rw-p 0014a000 08:01 10174818                   /lib/libc-2.5.so
2acc107f7000-2acc107fc000 rw-p 2acc107f7000 00:00 0 
2acc107fc000-2acc10821000 r-xp 00000000 08:01 13386048                   /usr/lib/libaudiofile.so.0.0.2
2acc10821000-2acc10a20000 ---p 00025000 08:01 13386048                   /usr/lib/libaudiofile.so.0.0.2
2acc10a20000-2acc10a24000 rw-p 00024000 08:01 13386048                   /usr/lib/libaudiofile.so.0.0.2
2acc10a24000-2acc10aa5000 r-xp 00000000 08:01 10174822                   /lib/libm-2.5.so
2acc10aa5000-2acc10ca4000 ---p 00081000 08:01 10174822                   /lib/libm-2.5.so
2acc10ca4000-2acc10ca6000 rw-p 00080000 08:01 10174822                   /lib/libm-2.5.so
2acc10ca6000-2acc10ca7000 rw-p 2acc10ca6000 00:00 0 
2acc10ca7000-2acc10d7d000 r-xp 00000000 08:01 13385977                   /usr/lib/libasound.so.2.0.0
2acc10d7d000-2acc10f7d000 ---p 000d6000 08:01 13385977                   /usr/lib/libasound.so.2.0.0
2acc10f7d000-2acc10f85000 rw-p 000d6000 08:01 13385977                   /usr/lib/libasound.so.2.0.0
2acc10f85000-2acc110bc000 r-xp 00000000 08:01 13386444                   /usr/lib/libxml2.so.2.6.27
2acc110bc000-2acc112bc000 ---p 00137000 08:01 13386444                   /usr/lib/libxml2.so.2.6.27
2acc112bc000-2acc112c5000 rw-p 00137000 08:01 13386444                   /usr/lib/libxml2.so.2.6.27
2acc112c5000-2acc112c6000 rw-p 2acc112c5000 00:00 0 
2acc112c6000-2acc11330000 r-xp 00000000 08:01 18415648                   /usr/lib/libbonoboui-2.so.0.0.0
2acc11330000-2acc1152f000 ---p 0006a000 08:01 18415648                   /usr/lib/libbonoboui-2.so.0.0.0
2acc1152f000-2acc11534000 rw-p 00069000 08:01 18415648                   /usr/lib/libbonoboui-2.so.0.0.0
2acc11534000-2acc11535000 rw-p 2acc11534000 00:00 0 
2acc11535000-2acc11562000 r-xp 00000000 08:01 13387207                   /usr/lib/libgnomecanvas-2.so.0.1400.0
2acc11562000-2acc11762000 ---p 0002d000 08:01 13387207                   /usr/lib/libgnomecanvas-2.so.0.1400.0
2acc11762000-2acc11764000 rw-p 0002d000 08:01 13387207                   /usr/lib/libgnomecanvas-2.so.0.1400.0
2acc11764000-2acc1176b000 r-xp 00000000 08:01 10174492                   /lib/libpopt.so.0.0.0
2acc1176b000-2acc1196b000 ---p 00007000 08:01 10174492                   /lib/libpopt.so.0.0.0
2acc1196b000-2acc1196c000 rw-p 00007000 08:01 10174492                   /lib/libpopt.so.0.0.0
2acc1196c000-2acc11981000 r-xp 00000000 08:01 13387026                   /usr/lib/libart_lgpl_2.so.2.3.17
2acc11981000-2acc11a80000 ---p 00015000 08:01 13387026                   /usr/lib/libart_lgpl_2.so.2.3.17
2acc11a80000-2acc11a83000 rw-p 00014000 08:01 13387026                   /usr/lib/libart_lgpl_2.so.2.3.17
2acc11a83000-2acc11a84000 rw-p 2acc11a83000 00:00 0 
2acc11a84000-2acc11ab2000 r-xp 00000000 08:01 13389510                   /usr/lib/libpangoft2-1.0.so.0.1600.2
2acc11ab2000-2acc11cb1000 ---p 0002e000 08:01 13389510                   /usr/lib/libpangoft2-1.0.so.0.1600.2
2acc11cb1000-2acc11cb2000 rw-p 0002d000 08:01 13389510                   /usr/lib/libpangoft2-1.0.so.0.1600.2
2acc11cb2000-2acc11cbb000 r-xp 00000000 08:01 13389509                   /usr/lib/libpangocairo-1.0.so.0.1600.2
2acc11cbb000-2acc11eba000 ---p 00009000 08:01 13389509                   /usr/lib/libpangocairo-1.0.so.0.1600.2
2acc11eba000-2acc11ebb000 rw-p 00008000 08:01 13389509                   /usr/lib/libpangocairo-1.0.so.0.1600.2
2acc11ebb000-2acc11ee5000 r-xp 00000000 08:01 13385989                   /usr/lib/libfontconfig.so.1.2.0
2acc11ee5000-2acc120e4000 ---p 0002a000 08:01 13385989                   /usr/lib/libfontconfig.so.1.2.0
2acc120e4000-2acc120ef000 rw-p 00029000 08:01 13385989                   /usr/lib/libfontconfig.so.1.2.0
2acc120ef000-2acc120f0000 rw-p 2acc120ef000 00:00 0 
2acc120f0000-2acc12100000 r-xp 00000000 08:01 13388030                   /usr/lib/libXext.so.6.4.0
2acc12100000-2acc12300000 ---p 00010000 08:01 13388030                   /usr/lib/libXext.so.6.4.0
2acc12300000-2acc12301000 rw-p 00010000 08:01 13388030                   /usr/lib/libXext.so.6.4.0
2acc12301000-2acc1230a000 r-xp 00000000 08:01 13386908                   /usr/lib/libXrender.so.1.3.0
2acc1230a000-2acc12509000 ---p 00009000 08:01 13386908                   /usr/lib/libXrender.so.1.3.0
2acc12509000-2acc1250a000 rw-p 00008000 08:01 13386908                   /usr/lib/libXrender.so.1.3.0
2acc1250a000-2acc1250c000 r-xp 00000000 08:01 13387501                   /usr/lib/libXinerama.so.1.0.0
2acc1250c000-2acc1260b000 ---p 00002000 08:01 13387501                   /usr/lib/libXinerama.so.1.0.0
2acc1260b000-2acc1260c000 rw-p 00001000 08:01 13387501                   /usr/lib/libXinerama.so.1.0.0
2acc1260c000-2acc1260d000 rw-p 2acc1260c000 00:00 0 
2acc1260d000-2acc12615000 r-xp 00000000 08:01 13388090                   /usr/lib/libXi.so.6.0.0
2acc12615000-2acc12815000 ---p 00008000 08:01 13388090                   /usr/lib/libXi.so.6.0.0
2acc12815000-2acc12816000 rw-p 00008000 08:01 13388090                   /usr/lib/libXi.so.6.0.0
2acc12816000-2acc12820000 r-xp 00000000 08:01 13389449                   /usr/lib/libXcursor.so.1.0.2
2acc12820000-2acc12a1f000 ---p 0000a000 08:01 13389449                   /usr/lib/libXcursor.so.1.0.2
2acc12a1f000-2acc12a20000 rw-p 00009000 08:01 13389449                   /usr/lib/libXcursor.so.1.0.2
2acc12a20000-2acc12a25000 r-xp 00000000 08:01 13387453                   /usr/lib/libXfixes.so.3.1.0
2acc12a25000-2acc12c24000 ---p 00005000 08:01 13387453                   /usr/lib/libXfixes.so.3.1.0
2acc12c24000-2acc12c25000 rw-p 00004000 08:01 13387453                   /usr/lib/libXfixes.so.3.1.0
2acc12c25000-2acc12c26000 rw-p 2acc12c25000 00:00 0 
2acc12c26000-2acc12c9a000 r-xp 00000000 08:01 13389505                   /usr/lib/libcairo.so.2.11.1
2acc12c9a000-2acc12e9a000 ---p 00074000 08:01 13389505                   /usr/lib/libcairo.so.2.11.1
2acc12e9a000-2acc12e9c000 rw-p 00074000 08:01 13389505                   /usr/lib/libcairo.so.2.11.1
2acc12e9c000-2acc12efe000 r-xp 00000000 08:01 13387343                   /usr/lib/libgnomevfs-2.so.0.1800.1
2acc12efe000-2acc130fe000 ---p 00062000 08:01 13387343                   /usr/lib/libgnomevfs-2.so.0.1800.1
2acc130fe000-2acc13103000 rw-p 00062000 08:01 13387343                   /usr/lib/libgnomevfs-2.so.0.1800.1
2acc13103000-2acc13106000 r-xp 00000000 08:01 13389476                   /usr/lib/libgmodule-2.0.so.0.1200.11
2acc13106000-2acc13305000 ---p 00003000 08:01 13389476                   /usr/lib/libgmodule-2.0.so.0.1200.11
2acc13305000-2acc13306000 rw-p 00002000 08:01 13389476                   /usr/lib/libgmodule-2.0.so.0.1200.11
2acc13306000-2acc13307000 rw-p 2acc13306000 00:00 0 
2acc13307000-2acc13309000 r-xp 00000000 08:01 10174821                   /lib/libdl-2.5.so
2acc13309000-2acc13509000 ---p 00002000 08:01 10174821                   /lib/libdl-2.5.so
2acc13509000-2acc1350b000 rw-p 00002000 08:01 10174821                   /lib/libdl-2.5.so
2acc1350b000-2acc1350f000 r-xp 00000000 08:01 13389477                   /usr/lib/libgthread-2.0.so.0.1200.11
2acc1350f000-2acc1370e000 ---p 00004000 08:01 13389477                   /usr/lib/libgthread-2.0.so.0.1200.11
2acc1370e000-2acc1370f000 rw-p 00003000 08:01 13389477                   /usr/lib/libgthread-2.0.so.0.1200.11
2acc1370f000-2acc13717000 r-xp 00000000 08:01 10174836                   /lib/librt-2.5.so
2acc13717000-2acc13916000 ---p 00008000 08:01 10174836                   /lib/librt-2.5.so
2acc13916000-2acc13918000 rw-p 00007000 08:01 10174836                   /lib/librt-2.5.so
2acc13918000-2acc13919000 rw-p 2acc13918000 00:00 0 
2acc13919000-2acc13922000 r-xp 00000000 08:01 18415656                   /usr/lib/libstartup-notification-1.so.0.0.0
2acc13922000-2acc13b21000 ---p 00009000 08:01 18415656                   /usr/lib/libstartup-notification-1.so.0.0.0
2acc13b21000-2acc13b22000 rw-p 00008000 08:01 18415656                   /usr/lib/libstartup-notification-1.so.0.0.0
2acc13b22000-2acc13b43000 r-xp 00000000 08:01 13387535                   /usr/lib/libjpeg.so.62.0.0
2acc13b43000-2acc13c43000 ---p 00021000 08:01 13387535                   /usr/lib/libjpeg.so.62.0.0
2acc13c43000-2acc13c44000 rw-p 00021000 08:01 13387535                   /usr/lib/libjpeg.so.62.0.0
2acc13c44000-2acc13c45000 rw-p 2acc13c44000 00:00 0 
2acc13c45000-2acc13c4a000 r-xp 00000000 08:01 13388020                   /usr/lib/libXdmcp.so.6.0.0
2acc13c4a000-2acc13e49000 ---p 00005000 08:01 13388020                   /usr/lib/libXdmcp.so.6.0.0
2acc13e49000-2acc13e4a000 rw-p 00004000 08:01 13388020                   /usr/lib/libXdmcp.so.6.0.0
2acc13e4a000-2acc13e4f000 r-xp 00000000 08:01 13387214                   /usr/lib/libORBitCosNaming-2.so.0.1.0
2acc13e4f000-2acc1404f000 ---p 00005000 08:01 13387214                   /usr/lib/libORBitCosNaming-2.so.0.1.0
2acc1404f000-2acc14051000 rw-p 00005000 08:01 13387214                   /usr/lib/libORBitCosNaming-2.so.0.1.0
2acc14051000-2acc14052000 rw-p 2acc14051000 00:00 0 
2acc14052000-2acc14066000 r-xp 00000000 08:01 10174824                   /lib/libnsl-2.5.so
2acc14066000-2acc14266000 ---p 00014000 08:01 10174824                   /lib/libnsl-2.5.so
2acc14266000-2acc14268000 rw-p 00014000 08:01 10174824                   /lib/libnsl-2.5.so
2acc14268000-2acc1426a000 rw-p 2acc14268000 00:00 0 
2acc1426a000-2acc14280000 r-xp 00000000 08:01 13387062                   /usr/lib/libz.so.1.2.3
2acc14280000-2acc1447f000 ---p 00016000 08:01 13387062                   /usr/lib/libz.so.1.2.3
2acc1447f000-2acc14480000 rw-p 00015000 08:01 13387062                   /usr/lib/libz.so.1.2.3
2acc14480000-2acc14481000 rw-p 2acc14480000 00:00 0 
2acc14481000-2acc144f5000 r-xp 00000000 08:01 13385943                   /usr/lib/libfreetype.so.6.3.10
2acc144f5000-2acc146f5000 ---p 00074000 08:01 13385943                   /usr/lib/libfreetype.so.6.3.10
2acc146f5000-2acc146fa000 rw-p 00074000 08:01 13385943                   /usr/lib/libfreetype.so.6.3.10
2acc146fa000-2acc1471b000 r-xp 00000000 08:01 13389451                   /usr/lib/libexpat.so.1.0.0
2acc1471b000-2acc1491a000 ---p 00021000 08:01 13389451                   /usr/lib/libexpat.so.1.0.0
2acc1491a000-2acc1491d000 rw-p 00020000 08:01 13389451                   /usr/lib/libexpat.so.1.0.0
2acc1491d000-2acc1491e000 rw-p 2acc1491d000 00:00 0 
2acc1491e000-2acc14942000 r-xp 00000000 08:01 13386679                   /usr/lib/libpng12.so.0.15.0
2acc14942000-2acc14b41000 ---p 00024000 08:01 13386679                   /usr/lib/libpng12.so.0.15.0
2acc14b41000-2acc14b42000 rw-p 00023000 08:01 13386679                   /usr/lib/libpng12.so.0.15.0
2acc14b42000-2acc14bb7000 r-xp 00000000 08:01 13389528                   /usr/lib/libgnutls.so.13.0.9
2acc14bb7000-2acc14db6000 ---p 00075000 08:01 13389528                   /usr/lib/libgnutls.so.13.0.9
2acc14db6000-2acc14dc1000 rw-p 00074000 08:01 13389528                   /usr/lib/libgnutls.so.13.0.9
2acc14dc1000-2acc14dc2000 rw-p 2acc14dc1000 00:00 0 
2acc14dc2000-2acc14dc5000 r-xp 00000000 08:01 13387322                   /usr/lib/libavahi-glib.so.1.0.1
2acc14dc5000-2acc14fc4000 ---p 00003000 08:01 13387322                   /usr/lib/libavahi-glib.so.1.0.1
2acc14fc4000-2acc14fc5000 rw-p 00002000 08:01 13387322                   /usr/lib/libavahi-glib.so.1.0.1
2acc14fc5000-2acc14fd0000 r-xp 00000000 08:01 13386249                   /usr/lib/libavahi-common.so.3.4.3
2acc14fd0000-2acc151d0000 ---p 0000b000 08:01 13386249                   /usr/lib/libavahi-common.so.3.4.3
2acc151d0000-2acc151d1000 rw-p 0000b000 08:01 13386249                   /usr/lib/libavahi-common.so.3.4.3
2acc151d1000-2acc151e0000 r-xp 00000000 08:01 13387181                   /usr/lib/libavahi-client.so.3.2.2
2acc151e0000-2acc153e0000 ---p 0000f000 08:01 13387181                   /usr/lib/libavahi-client.so.3.2.2
2acc153e0000-2acc153e1000 rw-p 0000f000 08:01 13387181                   /usr/lib/libavahi-client.so.3.2.2
2acc153e1000-2acc153e2000 rw-p 2acc153e1000 00:00 0 
2acc153e2000-2acc153f3000 r-xp 00000000 08:01 10174835                   /lib/libresolv-2.5.so
2acc153f3000-2acc155f3000 ---p 00011000 08:01 10174835                   /lib/libresolv-2.5.so
2acc155f3000-2acc155f5000 rw-p 00011000 08:01 10174835                   /lib/libresolv-2.5.so
2acc155f5000-2acc155f7000 rw-p 2acc155f5000 00:00 0 
2acc155f7000-2acc1560d000 r-xp 00000000 08:01 10174525                   /lib/libselinux.so.1
2acc1560d000-2acc1580c000 ---p 00016000 08:01 10174525                   /lib/libselinux.so.1
2acc1580c000-2acc1580e000 rw-p 00015000 08:01 10174525                   /lib/libselinux.so.1
2acc1580e000-2acc1580f000 rw-p 2acc1580e000 00:00 0 
2acc1580f000-2acc15811000 r-xp 00000000 08:01 10174839                   /lib/libutil-2.5.so
2acc15811000-2acc15a10000 ---p 00002000 08:01 10174839                   /lib/libutil-2.5.so
2acc15a10000-2acc15a12000 rw-p 00001000 08:01 10174839                   /lib/libutil-2.5.so
2acc15a12000-2acc15a13000 rw-p 2acc15a12000 00:00 0 
2acc15a13000-2acc15a28000 r-xp 00000000 08:01 13387183                   /usr/lib/libtasn1.so.3.0.6
2acc15a28000-2acc15c28000 ---p 00015000 08:01 13387183                   /usr/lib/libtasn1.so.3.0.6
2acc15c28000-2acc15c29000 rw-p 00015000 08:01 13387183                   /usr/lib/libtasn1.so.3.0.6
2acc15c29000-2acc15c73000 r-xp 00000000 08:01 13387298                   /usr/lib/libgcrypt.so.11.2.2
2acc15c73000-2acc15e73000 ---p 0004a000 08:01 13387298                   /usr/lib/libgcrypt.so.11.2.2
2acc15e73000-2acc15e75000 rw-p 0004a000 08:01 13387298                   /usr/lib/libgcrypt.so.11.2.2
2acc15e75000-2acc15e77000 rw-p 2acc15e75000 00:00 0 
2acc15e77000-2acc15e7a000 r-xp 00000000 08:01 13387053                   /usr/lib/libgpg-error.so.0.3.0
2acc15e7a000-2acc16079000 ---p 00003000 08:01 13387053                   /usr/lib/libgpg-error.so.0.3.0
2acc16079000-2acc1607a000 rw-p 00002000 08:01 13387053                   /usr/lib/libgpg-error.so.0.3.0
2acc1607a000-2acc160b5000 r-xp 00000000 08:01 10174518                   /lib/libsepol.so.1
2acc160b5000-2acc162b5000 ---p 0003b000 08:01 10174518                   /lib/libsepol.so.1
2acc162b5000-2acc162b6000 rw-p 0003b000 08:01 10174518                   /lib/libsepol.so.1
2acc162b6000-2acc162c4000 rw-p 2acc162b6000 00:00 0 
2acc162c4000-2acc162cb000 r-xp 00000000 08:01 10174825                   /lib/libnss_compat-2.5.so
2acc162cb000-2acc164cb000 ---p 00007000 08:01 10174825                   /lib/libnss_compat-2.5.so
2acc164cb000-2acc164cd000 rw-p 00007000 08:01 10174825                   /lib/libnss_compat-2.5.so
2acc164cd000-2acc164d7000 r-xp 00000000 08:01 10174829                   /lib/libnss_nis-2.5.so
2acc164d7000-2acc166d6000 ---p 0000a000 08:01 10174829                   /lib/libnss_nis-2.5.so
2acc166d6000-2acc166d8000 rw-p 00009000 08:01 10174829                   /lib/libnss_nis-2.5.so
2acc166d8000-2acc166e2000 r-xp 00000000 08:01 10174827                   /lib/libnss_files-2.5.so
2acc166e2000-2acc168e1000 ---p 0000a000 08:01 10174827                   /lib/libnss_files-2.5.so
2acc168e1000-2acc168e3000 rw-p 00009000 08:01 10174827                   /lib/libnss_files-2.5.so
2acc168e3000-2acc169ba000 r--p 00000000 08:01 13615567                   /usr/lib/locale/en_AU.utf8/LC_COLLATE
2acc169ba000-2acc169bb000 r--p 00000000 08:01 13615566                   /usr/lib/locale/en_AU.utf8/LC_TIME
2acc169bb000-2acc169bc000 r--p 00000000 08:01 13615565                   /usr/lib/locale/en_AU.utf8/LC_NUMERIC
2acc169bc000-2acc169f7000 r--p 00000000 08:01 13618640                   /usr/lib/locale/en_AU.utf8/LC_CTYPE
2acc169f7000-2acc16a06000 r--p 00000000 08:01 13747246                   /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20.mo
2acc16a06000-2acc16a0b000 r--p 00000000 08:01 13747247                   /usr/share/locale-langpack/en_AU/LC_MESSAGES/gtk20-properties.mo
2acc16a0b000-2acc16a0d000 r-xp 00000000 08:01 13403571                   /usr/lib/gconv/ISO8859-1.so
2acc16a0d000-2acc16c0c000 ---p 00002000 08:01 13403571                   /usr/lib/gconv/ISO8859-1.so
2acc16c0c000-2acc16c0e000 rw-p 00001000 08:01 13403571                   /usr/lib/gconv/ISO8859-1.so
2acc16c0e000-2acc16c12000 r--p 00000000 08:01 13747236                   /usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-session-2.0.mo
2acc16c12000-2acc16c19000 r--p 00000000 08:01 13747252                   /usr/share/locale-langpack/en_AU/LC_MESSAGES/libgnome-2.0.mo
2acc16c19000-2acc16c27000 r-xp 00000000 08:01 704516                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
2acc16c27000-2acc16e26000 ---p 0000e000 08:01 704516                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
2acc16e26000-2acc16e27000 rw-p 0000d000 08:01 704516                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
2acc16e27000-2acc16e2b000 r-xp 00000000 08:01 10174760                   /lib/libattr.so.1.1.0
2acc16e2b000-2acc1702a000 ---p 00004000 08:01 10174760                   /lib/libattr.so.1.1.0
2acc1702a000-2acc1702b000 rw-p 00003000 08:01 10174760                   /lib/libattr.so.1.1.0
2acc1702b000-2acc17031000 r-xp 00000000 08:01 10174744                   /lib/libacl.so.1.1.0
2acc17031000-2acc17230000 ---p 00006000 08:01 10174744                   /lib/libacl.so.1.1.0
2acc17230000-2acc17231000 rw-p 00005000 08:01 10174744                   /lib/libacl.so.1.1.0
2acc17231000-2acc17239000 r-xp 00000000 08:01 13387351                   /usr/lib/libfam.so.0.0.0
2acc17239000-2acc17438000 ---p 00008000 08:01 13387351                   /usr/lib/libfam.so.0.0.0
2acc17438000-2acc17439000 rw-p 00007000 08:01 13387351                   /usr/lib/libfam.so.0.0.0
2acc17439000-2acc1743b000 r--p 00000000 08:01 13747221                   /usr/share/locale-langpack/en_AU/LC_MESSAGES/gnome-desktop-2.0.mo
2acc1743b000-2acc1743f000 r--p 00000000 08:01 13747251                   /usr/share/locale-langpack/en_AU/LC_MESSAGES/glib20.mo
2acc17440000-2acc17444000 r-xp 00000000 08:01 13500657                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
2acc17444000-2acc17644000 ---p 00004000 08:01 13500657                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
2acc17644000-2acc17645000 rw-p 00004000 08:01 13500657                   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
2acc17645000-2acc176a5000 rw-s 00000000 00:08 393220                     /SYSV00000000 (deleted)
2acc176a5000-2acc176b8000 r-xp 00000000 08:01 13500557                   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
2acc176b8000-2acc178b8000 ---p 00013000 08:01 13500557                   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
2acc178b8000-2acc178b9000 rw-p 00013000 08:01 13500557                   /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
2acc178b9000-2acc17b10000 r--p 00000000 08:01 13715747                   /usr/share/icons/Tango/icon-theme.cache
2acc17b10000-2acc1948b000 r--p 00000000 08:01 13779118                   /usr/share/icons/crystalsvg/icon-theme.cache
2acc1948b000-2acc19a3f000 r--p 00000000 08:01 13713715                   /usr/share/icons/hicolor/icon-theme.cache
2acc19a3f000-2acc19a45000 r--s 00000000 08:01 4785370                    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2acc19a45000-2acc19a4b000 r--s 00000000 08:01 4785369                    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2acc19a4b000-2acc19a51000 r--s 00000000 08:01 4785456                    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2acc19a51000-2acc19a5d000 r--s 00000000 08:01 4786282                    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2acc19a5d000-2acc19a5f000 r--s 00000000 08:01 4786298                    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2acc19a5f000-2acc19a67000 r--s 00000000 08:01 4785459                    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2acc19a67000-2acc19a70000 r--s 00000000 08:01 4786284                    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2acc19a70000-2acc19a72000 r--s 00000000 08:01 4785461                    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2acc19a72000-2acc19a73000 r--s 00000000 08:01 4786283                    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2acc19a73000-2acc19a74000 r--s 00000000 08:01 4786299                    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2acc19a74000-2acc19a78000 r--s 00000000 08:01 4785464                    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2acc19a78000-2acc19a7b000 r--s 00000000 08:01 4785465                    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2acc19a7b000-2acc19a81000 r--s 00000000 08:01 4786300                    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2acc19a81000-2acc19a87000 r--s 00000000 08:01 4785467                    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2acc19a87000-2acc19a88000 r--s 00000000 08:01 4785468                    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2acc19a88000-2acc19a8b000 r--s 00000000 08:01 4786301                    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2acc19a8b000-2acc19a8d000 r--s 00000000 08:01 4785470                    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2acc19a8d000-2acc19a90000 r--s 00000000 08:01 4786302                    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2acc19a90000-2acc19a9b000 r--s 00000000 08:01 4785472                    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2acc19a9b000-2acc19a9f000 r--s 00000000 08:01 4785473                    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2acc19a9f000-2acc19aa2000 r--s 00000000 08:01 4785625                    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2acc19aa2000-2acc19aa3000 r--s 00000000 08:01 4786303                    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2acc19aa3000-2acc19aa4000 r--s 00000000 08:01 4785844                    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86-64.cache-2
2acc19aa4000-2acc19aa5000 r--s 00000000 08:01 4786397                    /var/cache/fontconfig/aa6caf9eb4374966b8da29da8547f4f4-x86-64.cache-2
2acc19aa5000-2acc19aa6000 r--s 00000000 08:01 4785858                    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86-64.cache-2
2acc19aa6000-2acc19aa8000 r--s 00000000 08:01 4785859                    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2acc19aa8000-2acc19aa9000 r--s 00000000 08:01 4786398                    /var/cache/fontconfig/c6c650a19da23b8ee5782aefc5f28033-x86-64.cache-2
2acc19aa9000-2acc19aaa000 r--s 00000000 08:01 4785860                    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2acc19aaa000-2acc19ab4000 r--s 00000000 08:01 4784294                    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2acc19ab4000-2acc19ab8000 r--s 00000000 08:01 4786279                    /var/cache/fontconfig/fac9d1061ce4dddb2143955f84876fd7-x86-64.cache-2
2acc19ab8000-2acc19abd000 r--s 00000000 08:01 4785302                    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2acc19abd000-2acc19ac1000 r--s 00000000 08:01 4785303                    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86-64.cache-2
2acc19ac1000-2acc19ac7000 r--s 00000000 08:01 4786281                    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86-64.cache-2
2acc19ac7000-2acc19ace000 r--s 00000000 08:01 4785336                    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2acc19ace000-2acc19ad1000 r--s 00000000 08:01 4785337                    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2acc19ad1000-2acc19af0000 r--s 00000000 08:01 4785339                    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2acc19af0000-2acc19af1000 r--s 00000000 08:01 4785340                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2acc19af1000-2acc19af9000 r--s 00000000 08:01 4785341                    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2acc19af9000-2acc19b04000 r--s 00000000 08:01 4785342                    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2acc19b04000-2acc19b07000 r--s 00000000 08:01 4785343                    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86-64.cache-2
2acc19b07000-2acc19b0a000 r--s 00000000 08:01 4785344                    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2acc19b0a000-2acc19b11000 r--s 00000000 08:01 4785345                    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2acc19b11000-2acc19b13000 r--s 00000000 08:01 4785346                    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86-64.cache-2
2acc19b13000-2acc19b15000 r--s 00000000 08:01 4785347                    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2acc19b15000-2acc19b17000 r--s 00000000 08:01 4785348                    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86-64.cache-2
2acc19b17000-2acc19b1a000 r--s 00000000 08:01 4785349                    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86-64.cache-2
2acc19b1a000-2acc19b1b000 r--s 00000000 08:01 4785350                    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2acc19b1b000-2acc19b1c000 r--s 00000000 08:01 4785351                    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2acc19b1c000-2acc19b21000 r--s 00000000 08:01 4785352                    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2acc19b21000-2acc19b22000 r--s 00000000 08:01 4785353                    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86-64.cache-2
2acc19b22000-2acc19b23000 r--s 00000000 08:01 4785354                    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86-64.cache-2
2acc19b23000-2acc19b26000 r--s 00000000 08:01 4785355                    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86-64.cache-2
2acc19b26000-2acc19b27000 r--s 00000000 08:01 4785356                    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86-64.cache-2
2acc19b27000-2acc19b2f000 r--s 00000000 08:01 4785360                    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2acc19b2f000-2acc19b32000 r-xp 00000000 08:01 13586733                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2acc19b32000-2acc19d31000 ---p 00003000 08:01 13586733                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2acc19d31000-2acc19d32000 rw-p 00002000 08:01 13586733                   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
2acc19d32000-2acc19daf000 r--p 00000000 08:01 13598831                   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7fff9e397000-7fff9e3ad000 rw-p 7fff9e397000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

(update-notifier:6171): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6172): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6173): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gedit:6176): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6178): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
Session management error: IO error occured opening connection

both the short and the long schmere came after I followed the suggestions  [here]("http://ubuntuforums.org/showthread.php?t=23467") 

I should mention that I'm running an amd64 architecture

Cheers,:popcorn:
T

---

### Post by ST.x on 2007-10-04
Just delete ~/.gnome2/session and login again

---

### Post by tzramsoy on 2007-10-05
so easy and yet so great a solution! Thanks!
:guitar:

---


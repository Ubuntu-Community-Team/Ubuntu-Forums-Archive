---
title: "[Sun Java 6 and 7] Java applet crashes with particular applet"
date: 2013-02-24
forum: Gaming &amp; Leisure
---

### Post by jivana on 2013-02-24
Every time I try to load this particular applet which displays a simulated football game on bundesliga.de, it crashes. I got as far as the log files, but am unable to find anything useful there.
This is in a x86, computer with Ubuntu 12.04. I have only Sun Java 7 installed, no other java, so there should not be conflicts, and all other applets on web sites work fine.
I hope someone can help. 
Here is apport.log:
```
ERROR: apport (pid 13722) Mon Feb 25 12:23:24 2013: called for pid 13577, signal 6
ERROR: apport (pid 13722) Mon Feb 25 12:23:24 2013: executable: /usr/lib/jvm/java-7-oracle/jre/bin/java (command line "/usr/lib/jvm/java-7-oracle/jre/bin/java -D__jvm_launched=16912189137 -D__applet_launched=16911995032 -Xbootclasspath/a:/usr/lib/jvm/java-7-oracle/jre/lib/deploy.jar:/usr/lib/jvm/java-7-oracle/jre/lib/javaws.jar:/usr/lib/jvm/java-7-oracle/jre/lib/plugin.jar -Djava.class.path=/usr/lib/jvm/java-7-oracle/jre/classes -Dsun.awt.warmup=true -Xmx256m -Dsun.java2d.noddraw=true -Dsun.awt.noerasebackground=true -Dsun.java2d.d3d=false -Dsun.java2d.opengl=false sun.plugin2.main.client.PluginMain write_pipe_name=/tmp/.com.sun.deploy.net.socket.2586.8029033615677261167.AF_UNIX")
ERROR: apport (pid 13722) Mon Feb 25 12:23:24 2013: debug: session gdbus call: (true,)

ERROR: apport (pid 13722) Mon Feb 25 12:23:30 2013: wrote report /var/crash/_usr_lib_jvm_java-7-oracle_jre_bin_java.1000.crash
```

Here the java crash log file __usr_lib_jvm_java-7-oracle_jre_bin_java.1000.crash:
```
ProblemType: Crash
Architecture: i386
CrashCounter: 1
Date: Mon Feb 25 12:23:24 2013
DistroRelease: Ubuntu 12.04
ExecutablePath: /usr/lib/jvm/java-7-oracle/jre/bin/java
ExecutableTimestamp: 1361393699
ProcCmdline: /usr/lib/jvm/java-7-oracle/jre/bin/java -D__jvm_launched=16912189137 -D__applet_launched=16911995032 -Xbootclasspath/a:/usr/lib/jvm/java-7-oracle/jre/lib/deploy.jar:/usr/lib/jvm/java-7-oracle/jre/lib/javaws.jar:/usr/lib/jvm/java-7-oracle/jre/lib/plugin.jar -Djava.class.path=/usr/lib/jvm/java-7-oracle/jre/classes -Dsun.awt.warmup=true -Xmx256m -Dsun.java2d.noddraw=true -Dsun.awt.noerasebackground=true -Dsun.java2d.d3d=false -Dsun.java2d.opengl=false sun.plugin2.main.client.PluginMain write_pipe_name=/tmp/.com.sun.deploy.net.socket.2586.8029033615677261167.AF_UNIX
ProcCwd: /home/[username]
ProcEnviron:
 LC_NUMERIC=en_AU.UTF-8
 LC_ADDRESS=en_AU.UTF-8
 PATH=(custom, no user)
 LC_TIME=en_AU.UTF-8
 LC_TELEPHONE=en_AU.UTF-8
 LC_NAME=en_AU.UTF-8
 LC_PAPER=en_AU.UTF-8
 LC_IDENTIFICATION=en_AU.UTF-8
 SHELL=/bin/bash
 LC_MONETARY=en_AU.UTF-8
 LC_MEASUREMENT=en_AU.UTF-8
 LANG=en_US.UTF-8
ProcMaps:
 00110000-00115000 r-xp 00000000 08:01 43423      /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
 00115000-00116000 r--p 00004000 08:01 43423      /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
 00116000-00117000 rw-p 00005000 08:01 43423      /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
 00117000-00118000 r-xp 00000000 08:01 42762      /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3200.3
 00118000-00119000 r--p 00000000 08:01 42762      /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3200.3
 00119000-0011a000 rw-p 00001000 08:01 42762      /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3200.3
 0011a000-0011b000 r-xp 00000000 00:00 0          [vdso]
 0011b000-002be000 r-xp 00000000 08:01 14951808   /lib/i386-linux-gnu/libc-2.15.so
 002be000-002c0000 r--p 001a3000 08:01 14951808   /lib/i386-linux-gnu/libc-2.15.so
 002c0000-002c1000 rw-p 001a5000 08:01 14951808   /lib/i386-linux-gnu/libc-2.15.so
 002c1000-002c4000 rw-p 00000000 00:00 0 
 002c4000-002ee000 r-xp 00000000 08:01 14951819   /lib/i386-linux-gnu/libm-2.15.so
 002ee000-002ef000 r--p 00029000 08:01 14951819   /lib/i386-linux-gnu/libm-2.15.so
 002ef000-002f0000 rw-p 0002a000 08:01 14951819   /lib/i386-linux-gnu/libm-2.15.so
 002f0000-002fa000 r-xp 00000000 08:01 14951816   /lib/i386-linux-gnu/libnss_nis-2.15.so
 002fa000-002fb000 r--p 00009000 08:01 14951816   /lib/i386-linux-gnu/libnss_nis-2.15.so
 002fb000-002fc000 rw-p 0000a000 08:01 14951816   /lib/i386-linux-gnu/libnss_nis-2.15.so
 002fc000-00317000 r-xp 00000000 08:01 5510640    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libdeploy.so
 00317000-00318000 rw-p 0001b000 08:01 5510640    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libdeploy.so
 00318000-0031c000 rw-p 00000000 00:00 0 
 0031c000-0032a000 r-xp 00000000 08:01 44722      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 0032a000-0032b000 r--p 0000d000 08:01 44722      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 0032b000-0032c000 rw-p 0000e000 08:01 44722      /usr/lib/i386-linux-gnu/libXi.so.6.1.0
 0032c000-00331000 r-xp 00000000 08:01 45461      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 00331000-00332000 r--p 00004000 08:01 45461      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 00332000-00333000 rw-p 00005000 08:01 45461      /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
 00333000-00335000 r-xp 00000000 08:01 47797      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 00335000-00336000 r--p 00001000 08:01 47797      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 00336000-00337000 rw-p 00002000 08:01 47797      /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
 00337000-0033e000 r-xp 00000000 08:01 45027      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 0033e000-0033f000 r--p 00006000 08:01 45027      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 0033f000-00340000 rw-p 00007000 08:01 45027      /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
 00340000-00341000 r-xp 00000000 08:01 5510629    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libjawt.so
 00341000-00342000 rw-p 00000000 08:01 5510629    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libjawt.so
 00342000-00365000 r-xp 00000000 08:01 5510647    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libjava.so
 00365000-00366000 rw-p 00023000 08:01 5510647    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libjava.so
 00366000-00368000 r-xp 00000000 08:01 48277      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 00368000-00369000 r--p 00001000 08:01 48277      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 00369000-0036a000 rw-p 00002000 08:01 48277      /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
 0036a000-00372000 r-xp 00000000 08:01 43487      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 00372000-00373000 r--p 00008000 08:01 43487      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 00373000-00374000 rw-p 00009000 08:01 43487      /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
 00374000-00388000 r-xp 00000000 08:01 14943092   /lib/i386-linux-gnu/libz.so.1.2.3.4
 00388000-00389000 r--p 00013000 08:01 14943092   /lib/i386-linux-gnu/libz.so.1.2.3.4
 00389000-0038a000 rw-p 00014000 08:01 14943092   /lib/i386-linux-gnu/libz.so.1.2.3.4
 0038a000-0038c000 r-xp 00000000 08:01 46381      /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
 0038c000-0038d000 r--p 00001000 08:01 46381      /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
 0038d000-0038e000 rw-p 00002000 08:01 46381      /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
 0038e000-00399000 r-xp 00000000 08:01 5510619    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libverify.so
 00399000-0039a000 rw-p 0000b000 08:01 5510619    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libverify.so
 0039a000-00420000 r-xp 00000000 08:01 5510666    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libawt.so
 00420000-00427000 rw-p 00086000 08:01 5510666    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libawt.so
 00427000-0044b000 rw-p 00000000 00:00 0 
 0044b000-00494000 r-xp 00000000 08:01 5510617    /usr/lib/jvm/java-7-oracle/jre/lib/i386/xawt/libmawt.so
 00494000-00497000 rw-p 00048000 08:01 5510617    /usr/lib/jvm/java-7-oracle/jre/lib/i386/xawt/libmawt.so
 00497000-004c1000 r-xp 00000000 08:01 45846      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3000.0
 004c1000-004c2000 r--p 00029000 08:01 45846      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3000.0
 004c2000-004c3000 rw-p 0002a000 08:01 45846      /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3000.0
 004c3000-004f5000 r-xp 00000000 08:01 42580      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
 004f5000-004f6000 r--p 00032000 08:01 42580      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
 004f6000-004f7000 rw-p 00033000 08:01 42580      /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
 004f7000-004f8000 r-xp 00000000 08:01 42743      /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 004f8000-004f9000 r--p 00000000 08:01 42743      /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 004f9000-004fa000 rw-p 00001000 08:01 42743      /usr/lib/i386-linux-gnu/libX11-xcb.so.1.0.0
 004fa000-004fc000 r-xp 00000000 08:01 44641      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 004fc000-004fd000 r--p 00001000 08:01 44641      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 004fd000-004fe000 rw-p 00002000 08:01 44641      /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
 004fe000-00507000 r-xp 00000000 08:01 45019      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 00507000-00508000 r--p 00008000 08:01 45019      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 00508000-00509000 rw-p 00009000 08:01 45019      /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
 00509000-0050c000 r-xp 00000000 08:01 44310      /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 0050c000-0050d000 r--p 00002000 08:01 44310      /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 0050d000-0050e000 rw-p 00003000 08:01 44310      /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.3
 0050e000-00513000 r-xp 00000000 08:01 42846      /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00513000-00514000 r--p 00004000 08:01 42846      /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00514000-00515000 rw-p 00005000 08:01 42846      /usr/lib/i386-linux-gnu/libffi.so.6.0.0
 00515000-0051c000 r-xp 00000000 08:01 42701      /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 0051c000-0051d000 r--p 00006000 08:01 42701      /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 0051d000-0051e000 rw-p 00007000 08:01 42701      /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
 0051e000-0051f000 rwxp 00000000 00:00 0 
 00521000-00538000 r-xp 00000000 08:01 5510651    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libzip.so
 00538000-00539000 rw-p 00017000 08:01 5510651    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libzip.so
 00539000-00669000 r-xp 00000000 08:01 45110      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 00669000-0066a000 r--p 0012f000 08:01 45110      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 0066a000-0066c000 rw-p 00130000 08:01 45110      /usr/lib/i386-linux-gnu/libX11.so.6.3.0
 0066c000-0066d000 rw-p 00000000 00:00 0 
 0066d000-00718000 r-xp 00000000 08:01 47345      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
 00718000-00719000 ---p 000ab000 08:01 47345      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
 00719000-0071b000 r--p 000ab000 08:01 47345      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
 0071b000-0071c000 rw-p 000ad000 08:01 47345      /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
 0071c000-007e3000 r-xp 00000000 08:01 44948      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
 007e3000-007e4000 r--p 000c7000 08:01 44948      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
 007e4000-007e5000 rw-p 000c8000 08:01 44948      /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
 007e5000-007e7000 rw-p 00000000 00:00 0 
 007e7000-00834000 r-xp 00000000 08:01 44596      /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00834000-00835000 r--p 0004c000 08:01 44596      /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00835000-00836000 rw-p 0004d000 08:01 44596      /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.3
 00836000-00846000 r-xp 00000000 08:01 44190      /usr/lib/liboverlay-scrollbar-0.2.so.0.0.16
 00846000-00847000 r--p 0000f000 08:01 44190      /usr/lib/liboverlay-scrollbar-0.2.so.0.0.16
 00847000-00848000 rw-p 00010000 08:01 44190      /usr/lib/liboverlay-scrollbar-0.2.so.0.0.16
 0084b000-00852000 r-xp 00000000 08:01 14951810   /lib/i386-linux-gnu/libnss_compat-2.15.so
 00852000-00853000 r--p 00006000 08:01 14951810   /lib/i386-linux-gnu/libnss_compat-2.15.so
 00853000-00854000 rw-p 00007000 08:01 14951810   /lib/i386-linux-gnu/libnss_compat-2.15.so
 00854000-00871000 r-xp 00000000 08:01 14943044   /lib/i386-linux-gnu/libselinux.so.1
 00871000-00872000 r--p 0001c000 08:01 14943044   /lib/i386-linux-gnu/libselinux.so.1
 00872000-00873000 rw-p 0001d000 08:01 14943044   /lib/i386-linux-gnu/libselinux.so.1
 00875000-00878000 r-xp 00000000 08:01 14951823   /lib/i386-linux-gnu/libdl-2.15.so
 00878000-00879000 r--p 00002000 08:01 14951823   /lib/i386-linux-gnu/libdl-2.15.so
 00879000-0087a000 rw-p 00003000 08:01 14951823   /lib/i386-linux-gnu/libdl-2.15.so
 0087a000-008a2000 r-xp 00000000 08:01 14942296   /lib/i386-linux-gnu/libpng12.so.0.46.0
 008a2000-008a3000 r--p 00027000 08:01 14942296   /lib/i386-linux-gnu/libpng12.so.0.46.0
 008a3000-008a4000 rw-p 00028000 08:01 14942296   /lib/i386-linux-gnu/libpng12.so.0.46.0
 008a4000-008a9000 r-xp 00000000 08:01 75898      /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
 008a9000-008aa000 r--p 00004000 08:01 75898      /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
 008aa000-008ab000 rw-p 00005000 08:01 75898      /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
 008ab000-008af000 r-xp 00000000 08:01 46842      /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.8
 008af000-008b0000 r--p 00003000 08:01 46842      /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.8
 008b0000-008b1000 rw-p 00004000 08:01 46842      /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.8
 008b1000-008b3000 r-xp 00000000 08:01 14946219   /lib/libnss_mdns4_minimal.so.2
 008b3000-008b4000 r--p 00001000 08:01 14946219   /lib/libnss_mdns4_minimal.so.2
 008b4000-008b5000 rw-p 00002000 08:01 14946219   /lib/libnss_mdns4_minimal.so.2
 008b6000-008cc000 r-xp 00000000 08:01 14951828   /lib/i386-linux-gnu/libnsl-2.15.so
 008cc000-008cd000 r--p 00015000 08:01 14951828   /lib/i386-linux-gnu/libnsl-2.15.so
 008cd000-008ce000 rw-p 00016000 08:01 14951828   /lib/i386-linux-gnu/libnsl-2.15.so
 008ce000-008d0000 rw-p 00000000 00:00 0 
 008d0000-008d8000 r-xp 00000000 08:01 46649      /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 008d8000-008d9000 r--p 00007000 08:01 46649      /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 008d9000-008da000 rw-p 00008000 08:01 46649      /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
 008df000-008e1000 r-xp 00000000 08:01 44864      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 008e1000-008e2000 r--p 00001000 08:01 44864      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 008e2000-008e3000 rw-p 00002000 08:01 44864      /usr/lib/i386-linux-gnu/libXau.so.6.0.0
 008e8000-00907000 r-xp 00000000 08:01 44637      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 00907000-00908000 r--p 0001f000 08:01 44637      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 00908000-00909000 rw-p 00020000 08:01 44637      /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
 00909000-00911000 r-xp 00000000 08:01 48364      /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 00911000-00912000 r--p 00008000 08:01 48364      /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 00912000-00913000 rw-p 00009000 08:01 48364      /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
 00916000-0092a000 r-xp 00000000 08:01 5510658    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnet.so
 0092a000-0092b000 rw-p 00014000 08:01 5510658    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnet.so
 0092b000-0093e000 r-xp 00000000 08:01 14951813   /lib/i386-linux-gnu/libresolv-2.15.so
 0093e000-0093f000 ---p 00013000 08:01 14951813   /lib/i386-linux-gnu/libresolv-2.15.so
 0093f000-00940000 r--p 00013000 08:01 14951813   /lib/i386-linux-gnu/libresolv-2.15.so
 00940000-00941000 rw-p 00014000 08:01 14951813   /lib/i386-linux-gnu/libresolv-2.15.so
 00941000-00943000 rw-p 00000000 00:00 0 
 00943000-00958000 r-xp 00000000 08:01 120061     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 00958000-00959000 r--p 00014000 08:01 120061     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 00959000-0095a000 rw-p 00015000 08:01 120061     /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
 0095a000-0095c000 r-xp 00000000 08:01 47808      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 0095c000-0095d000 r--p 00001000 08:01 47808      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 0095d000-0095e000 rw-p 00002000 08:01 47808      /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
 0095e000-00984000 r-xp 00000000 08:01 14942247   /lib/i386-linux-gnu/libexpat.so.1.5.2
 00984000-00985000 ---p 00026000 08:01 14942247   /lib/i386-linux-gnu/libexpat.so.1.5.2
 00985000-00987000 r--p 00026000 08:01 14942247   /lib/i386-linux-gnu/libexpat.so.1.5.2
 00987000-00988000 rw-p 00028000 08:01 14942247   /lib/i386-linux-gnu/libexpat.so.1.5.2
 00988000-0098e000 r-xp 00000000 08:01 44925      /usr/lib/i386-linux-gnu/libogg.so.0.7.1
 0098e000-0098f000 r--p 00005000 08:01 44925      /usr/lib/i386-linux-gnu/libogg.so.0.7.1
 0098f000-00990000 rw-p 00006000 08:01 44925      /usr/lib/i386-linux-gnu/libogg.so.0.7.1
 00990000-00994000 r-xp 00000000 08:01 45022      /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
 00994000-00995000 r--p 00003000 08:01 45022      /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
 00995000-00996000 rw-p 00004000 08:01 45022      /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
 00996000-009a1000 r-xp 00000000 08:01 42277      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3000.0
 009a1000-009a2000 r--p 0000a000 08:01 42277      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3000.0
 009a2000-009a3000 rw-p 0000b000 08:01 42277      /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3000.0
 009a3000-009dd000 r-xp 00000000 08:01 14943072   /lib/i386-linux-gnu/libpcre.so.3.12.1
 009dd000-009de000 r--p 00039000 08:01 14943072   /lib/i386-linux-gnu/libpcre.so.3.12.1
 009de000-009df000 rw-p 0003a000 08:01 14943072   /lib/i386-linux-gnu/libpcre.so.3.12.1
 009df000-009e5000 r-xp 00000000 08:01 78166      /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
 009e5000-009e6000 r--p 00005000 08:01 78166      /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
 009e6000-009e7000 rw-p 00006000 08:01 78166      /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
 009ed000-009f1000 r-xp 00000000 08:01 48274      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 009f1000-009f2000 r--p 00004000 08:01 48274      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 009f2000-009f3000 rw-p 00005000 08:01 48274      /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
 009f3000-00a0f000 r-xp 00000000 08:01 14943039   /lib/i386-linux-gnu/libgcc_s.so.1
 00a0f000-00a10000 r--p 0001b000 08:01 14943039   /lib/i386-linux-gnu/libgcc_s.so.1
 00a10000-00a11000 rw-p 0001c000 08:01 14943039   /lib/i386-linux-gnu/libgcc_s.so.1
 00a11000-00a16000 r-xp 00000000 08:01 4328887    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/menuproxies/libappmenu.so
 00a16000-00a17000 r--p 00004000 08:01 4328887    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/menuproxies/libappmenu.so
 00a17000-00a18000 rw-p 00005000 08:01 4328887    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/menuproxies/libappmenu.so
 00a1a000-00a28000 r-xp 00000000 08:01 14942233   /lib/i386-linux-gnu/libudev.so.0.13.0
 00a28000-00a29000 r--p 0000e000 08:01 14942233   /lib/i386-linux-gnu/libudev.so.0.13.0
 00a29000-00a2a000 rw-p 0000f000 08:01 14942233   /lib/i386-linux-gnu/libudev.so.0.13.0
 00a2a000-00a2f000 r-xp 00000000 08:01 14951814   /lib/i386-linux-gnu/libnss_dns-2.15.so
 00a2f000-00a30000 r--p 00004000 08:01 14951814   /lib/i386-linux-gnu/libnss_dns-2.15.so
 00a30000-00a31000 rw-p 00005000 08:01 14951814   /lib/i386-linux-gnu/libnss_dns-2.15.so
 00a37000-00a56000 r-xp 00000000 08:01 45089      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2600.1
 00a56000-00a57000 r--p 0001e000 08:01 45089      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2600.1
 00a57000-00a58000 rw-p 0001f000 08:01 45089      /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2600.1
 00a58000-00a67000 r-xp 00000000 08:01 42558      /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 00a67000-00a68000 r--p 0000e000 08:01 42558      /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 00a68000-00a69000 rw-p 0000f000 08:01 42558      /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
 00a6a000-00a7d000 r-xp 00000000 08:01 5510674    /usr/lib/jvm/java-7-oracle/jre/lib/i386/jli/libjli.so
 00a7d000-00a7e000 rw-p 00012000 08:01 5510674    /usr/lib/jvm/java-7-oracle/jre/lib/i386/jli/libjli.so
 00a7e000-00aa7000 r-xp 00000000 08:01 44883      /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 00aa7000-00aa8000 r--p 00028000 08:01 44883      /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 00aa8000-00aa9000 rw-p 00029000 08:01 44883      /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
 00aa9000-00af0000 r-xp 00000000 08:01 14942299   /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00af0000-00af1000 r--p 00047000 08:01 14942299   /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00af1000-00af2000 rw-p 00048000 08:01 14942299   /lib/i386-linux-gnu/libdbus-1.so.3.5.8
 00af6000-00afd000 r-xp 00000000 08:01 14951815   /lib/i386-linux-gnu/librt-2.15.so
 00afd000-00afe000 r--p 00006000 08:01 14951815   /lib/i386-linux-gnu/librt-2.15.so
 00afe000-00aff000 rw-p 00007000 08:01 14951815   /lib/i386-linux-gnu/librt-2.15.so
 00aff000-00b10000 r-xp 00000000 08:01 44996      /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
 00b10000-00b11000 r--p 00010000 08:01 44996      /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
 00b11000-00b12000 rw-p 00011000 08:01 44996      /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
 00b12000-00b1b000 r-xp 00000000 08:01 9603       /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.0
 00b1b000-00b1c000 r--p 00008000 08:01 9603       /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.0
 00b1c000-00b1d000 rw-p 00009000 08:01 9603       /usr/lib/i386-linux-gnu/libpciaccess.so.0.11.0
 00b1e000-00b2e000 r-xp 00000000 08:01 43989      /usr/lib/i386-linux-gnu/gio/modules/libgioremote-volume-monitor.so
 00b2e000-00b2f000 r--p 0000f000 08:01 43989      /usr/lib/i386-linux-gnu/gio/modules/libgioremote-volume-monitor.so
 00b2f000-00b30000 rw-p 00010000 08:01 43989      /usr/lib/i386-linux-gnu/gio/modules/libgioremote-volume-monitor.so
 00b30000-00b3b000 r-xp 00000000 08:01 12686      /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 00b3b000-00b3c000 r--p 0000a000 08:01 12686      /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 00b3c000-00b3d000 rw-p 0000b000 08:01 12686      /usr/lib/i386-linux-gnu/libdrm.so.2.4.0
 00b3f000-00b4f000 r-xp 00000000 08:01 46997      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 00b4f000-00b50000 r--p 0000f000 08:01 46997      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 00b50000-00b51000 rw-p 00010000 08:01 46997      /usr/lib/i386-linux-gnu/libXext.so.6.4.0
 00b51000-00b7a000 r-xp 00000000 08:01 47255      /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 00b7a000-00b7b000 r--p 00028000 08:01 47255      /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 00b7b000-00b7c000 rw-p 00029000 08:01 47255      /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
 00b7c000-00b8d000 r-xp 00000000 08:01 43589      /usr/lib/i386-linux-gnu/libdbusmenu-gtk.so.4.0.13
 00b8d000-00b8e000 r--p 00010000 08:01 43589      /usr/lib/i386-linux-gnu/libdbusmenu-gtk.so.4.0.13
 00b8e000-00b8f000 rw-p 00011000 08:01 43589      /usr/lib/i386-linux-gnu/libdbusmenu-gtk.so.4.0.13
 00b8f000-00ba9000 r-xp 00000000 08:01 44725      /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.13
 00ba9000-00baa000 r--p 00019000 08:01 44725      /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.13
 00baa000-00bab000 rw-p 0001a000 08:01 44725      /usr/lib/i386-linux-gnu/libdbusmenu-glib.so.4.0.13
 00bad000-00bc4000 r-xp 00000000 08:01 14951817   /lib/i386-linux-gnu/libpthread-2.15.so
 00bc4000-00bc5000 r--p 00016000 08:01 14951817   /lib/i386-linux-gnu/libpthread-2.15.so
 00bc5000-00bc6000 rw-p 00017000 08:01 14951817   /lib/i386-linux-gnu/libpthread-2.15.so
 00bc6000-00bc8000 rw-p 00000000 00:00 0 
 00bc8000-00cbf000 r-xp 00000000 08:01 14946136   /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00cbf000-00cc0000 r--p 000f6000 08:01 14946136   /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00cc0000-00cc1000 rw-p 000f7000 08:01 14946136   /lib/i386-linux-gnu/libglib-2.0.so.0.3200.3
 00cc1000-00cf6000 r-xp 00000000 08:01 77675      /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so
 00cf6000-00cf7000 r--p 00034000 08:01 77675      /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so
 00cf7000-00cf8000 rw-p 00035000 08:01 77675      /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libmurrine.so
 00cfc000-00d04000 r-xp 00000000 08:01 50783      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 00d04000-00d05000 r--p 00007000 08:01 50783      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 00d05000-00d06000 rw-p 00008000 08:01 50783      /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
 00d06000-00d48000 r-xp 00000000 08:01 5510669    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libfontmanager.so
 00d48000-00d4b000 rw-p 00041000 08:01 5510669    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libfontmanager.so
 00d4b000-00d4f000 rw-p 00000000 00:00 0 
 00d4f000-00d74000 r-xp 00000000 08:01 5510671    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libdcpr.so
 00d74000-00d77000 rw-p 00024000 08:01 5510671    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libdcpr.so
 00d77000-00d7d000 r-xp 00000000 08:01 46726      /usr/lib/i386-linux-gnu/libjson.so.0.0.1
 00d7d000-00d7e000 r--p 00005000 08:01 46726      /usr/lib/i386-linux-gnu/libjson.so.0.0.1
 00d7e000-00d7f000 rw-p 00006000 08:01 46726      /usr/lib/i386-linux-gnu/libjson.so.0.0.1
 00d85000-00d93000 r-xp 00000000 08:01 5510610    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnio.so
 00d93000-00d94000 rw-p 0000e000 08:01 5510610    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnio.so
 00d94000-00da3000 r-xp 00000000 08:01 19090      /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 00da3000-00da5000 r--p 0000f000 08:01 19090      /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 00da5000-00daa000 rwxp 00011000 08:01 19090      /usr/lib/i386-linux-gnu/libglapi.so.0.0.0
 00daa000-00db2000 r-xp 00000000 08:01 14942346   /lib/i386-linux-gnu/libwrap.so.0.7.6
 00db2000-00db3000 r--p 00007000 08:01 14942346   /lib/i386-linux-gnu/libwrap.so.0.7.6
 00db3000-00db4000 rw-p 00008000 08:01 14942346   /lib/i386-linux-gnu/libwrap.so.0.7.6
 00db4000-00db9000 r-xp 00000000 08:01 46403      /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
 00db9000-00dba000 r--p 00004000 08:01 46403      /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
 00dba000-00dbb000 rw-p 00005000 08:01 46403      /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
 00dbe000-00e05000 r-xp 00000000 08:01 42274      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
 00e05000-00e06000 ---p 00047000 08:01 42274      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
 00e06000-00e07000 r--p 00047000 08:01 42274      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
 00e07000-00e08000 rw-p 00048000 08:01 42274      /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
 00e08000-00e1e000 r-xp 00000000 08:01 46584      /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
 00e1e000-00e1f000 r--p 00016000 08:01 46584      /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
 00e1f000-00e20000 rw-p 00017000 08:01 46584      /usr/lib/i386-linux-gnu/libxcb-glx.so.0.0.0
 00e3f000-00e4a000 r-xp 00000000 08:01 14951812   /lib/i386-linux-gnu/libnss_files-2.15.so
 00e4a000-00e4b000 r--p 0000a000 08:01 14951812   /lib/i386-linux-gnu/libnss_files-2.15.so
 00e4b000-00e4c000 rw-p 0000b000 08:01 14951812   /lib/i386-linux-gnu/libnss_files-2.15.so
 00e4c000-00e90000 r-xp 00000000 08:01 43772      /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
 00e90000-00e91000 r--p 00043000 08:01 43772      /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
 00e91000-00e92000 rw-p 00044000 08:01 43772      /usr/lib/i386-linux-gnu/libibus-1.0.so.0.401.0
 00eb2000-00ecf000 r-xp 00000000 08:01 46130      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20409.1
 00ecf000-00ed1000 r--p 0001c000 08:01 46130      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20409.1
 00ed1000-00ed2000 rw-p 0001e000 08:01 46130      /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20409.1
 00edd000-00efd000 r-xp 00000000 08:01 14951820   /lib/i386-linux-gnu/ld-2.15.so
 00efd000-00efe000 r--p 0001f000 08:01 14951820   /lib/i386-linux-gnu/ld-2.15.so
 00efe000-00eff000 rw-p 00020000 08:01 14951820   /lib/i386-linux-gnu/ld-2.15.so
 00eff000-016b8000 r-xp 00000000 08:01 5510681    /usr/lib/jvm/java-7-oracle/jre/lib/i386/server/libjvm.so
 016b8000-0170a000 rw-p 007b9000 08:01 5510681    /usr/lib/jvm/java-7-oracle/jre/lib/i386/server/libjvm.so
 0170a000-01b2c000 rw-p 00000000 00:00 0 
 01b2c000-01b8c000 r-xp 00000000 08:01 5510628    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libt2k.so
 01b8c000-01b90000 rw-p 0005f000 08:01 5510628    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libt2k.so
 01b90000-01b94000 rw-p 00000000 00:00 0 
 01bb0000-01c43000 r-xp 00000000 08:01 43775      /usr/lib/i386-linux-gnu/libpixman-1.so.0.24.4
 01c43000-01c47000 r--p 00092000 08:01 43775      /usr/lib/i386-linux-gnu/libpixman-1.so.0.24.4
 01c47000-01c48000 rw-p 00096000 08:01 43775      /usr/lib/i386-linux-gnu/libpixman-1.so.0.24.4
 01c48000-01c7b000 r-xp 00000000 08:01 5510667    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libsunec.so
 01c7b000-01c7f000 rw-p 00032000 08:01 5510667    /usr/lib/jvm/java-7-oracle/jre/lib/i386/libsunec.so
 01c7f000-01c83000 rw-p 00000000 00:00 0 
 01c83000-01cde000 r-xp 00000000 00:14 5509091    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/natives/liblwjgl.so
 01cde000-01cdf000 r--p 0005a000 00:14 5509091    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/natives/liblwjgl.so
 01cdf000-01ce0000 rw-p 0005b000 00:14 5509091    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/natives/liblwjgl.so
 01ce0000-01f3c000 r-xp 00000000 08:01 18786      /usr/lib/i386-linux-gnu/dri/libdricore.so
 01f3c000-01f3d000 ---p 0025c000 08:01 18786      /usr/lib/i386-linux-gnu/dri/libdricore.so
 01f3d000-01f43000 r--p 0025c000 08:01 18786      /usr/lib/i386-linux-gnu/dri/libdricore.so
 01f43000-01f45000 rw-p 00262000 08:01 18786      /usr/lib/i386-linux-gnu/dri/libdricore.so
 01f45000-01f5a000 rw-p 00000000 00:00 0 
 01f5a000-01fbd000 r-xp 00000000 08:01 12594      /usr/lib/i386-linux-gnu/libpulsecommon-1.1.so
 01fbd000-01fbe000 r--p 00062000 08:01 12594      /usr/lib/i386-linux-gnu/libpulsecommon-1.1.so
 01fbe000-01fbf000 rw-p 00063000 08:01 12594      /usr/lib/i386-linux-gnu/libpulsecommon-1.1.so
 01fbf000-0202b000 r-xp 00000000 08:01 48377      /usr/lib/i386-linux-gnu/libsndfile.so.1.0.25
 0202b000-0202c000 r--p 0006c000 08:01 48377      /usr/lib/i386-linux-gnu/libsndfile.so.1.0.25
 0202c000-0202d000 rw-p 0006d000 08:01 48377      /usr/lib/i386-linux-gnu/libsndfile.so.1.0.25
 0202d000-02031000 rw-p 00000000 00:00 0 
 02051000-02129000 r-xp 00000000 08:01 46614      /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 02129000-0212a000 ---p 000d8000 08:01 46614      /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 0212a000-0212e000 r--p 000d8000 08:01 46614      /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 0212e000-0212f000 rw-p 000dc000 08:01 46614      /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
 0212f000-02136000 rw-p 00000000 00:00 0 
 02136000-0229c000 r-xp 00000000 08:01 46674      /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
 0229c000-022ad000 r--p 00165000 08:01 46674      /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
 022ad000-022ae000 rw-p 00176000 08:01 46674      /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
 02a91000-02b6c000 r-xp 00000000 08:01 18834      /usr/lib/i386-linux-gnu/dri/i965_dri.so
 02b6c000-02b6e000 r--p 000da000 08:01 18834      /usr/lib/i386-linux-gnu/dri/i965_dri.so
 02b6e000-02b70000 rw-p 000dc000 08:01 18834      /usr/lib/i386-linux-gnu/dri/i965_dri.so
 02b70000-02b71000 rw-p 00000000 00:00 0 
 02f61000-03076000 r-xp 00000000 08:01 18850      /usr/lib/i386-linux-gnu/dri/libglsl.so
 03076000-0307b000 r--p 00114000 08:01 18850      /usr/lib/i386-linux-gnu/dri/libglsl.so
 0307b000-0307d000 rw-p 00119000 08:01 18850      /usr/lib/i386-linux-gnu/dri/libglsl.so
 0307d000-0307e000 rw-p 00000000 00:00 0 
 036ec000-0373e000 r-xp 00000000 08:01 19024      /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2
 0373e000-03740000 r--p 00051000 08:01 19024      /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2
 03740000-03745000 rwxp 00053000 08:01 19024      /usr/lib/i386-linux-gnu/mesa/libGL.so.1.2
 04b54000-04be9000 r-xp 00000000 08:01 22632      /usr/lib/i386-linux-gnu/libfreetype.so.6.8.0
 04be9000-04bed000 r--p 00094000 08:01 22632      /usr/lib/i386-linux-gnu/libfreetype.so.6.8.0
 04bed000-04bee000 rw-p 00098000 08:01 22632      /usr/lib/i386-linux-gnu/libfreetype.so.6.8.0
 05ac4000-05f24000 r-xp 00000000 08:01 47343      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10
 05f24000-05f28000 r--p 00460000 08:01 47343      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10
 05f28000-05f2a000 rw-p 00464000 08:01 47343      /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10
 05f2a000-05f2c000 rw-p 00000000 00:00 0 
 068be000-0690a000 r-xp 00000000 08:01 12934      /usr/lib/i386-linux-gnu/libpulse.so.0.13.5
 0690a000-0690b000 r--p 0004b000 08:01 12934      /usr/lib/i386-linux-gnu/libpulse.so.0.13.5
 0690b000-0690c000 rw-p 0004c000 08:01 12934      /usr/lib/i386-linux-gnu/libpulse.so.0.13.5
 07a9e000-07ae9000 r-xp 00000000 00:14 5509093    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/natives/libopenal.so
 07ae9000-07aea000 r--p 0004b000 00:14 5509093    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/natives/libopenal.so
 07aea000-07aeb000 rw-p 0004c000 00:14 5509093    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/natives/libopenal.so
 07c52000-07da5000 r-xp 00000000 08:01 44308      /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 07da5000-07da7000 r--p 00153000 08:01 44308      /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 07da7000-07da8000 rw-p 00155000 08:01 44308      /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.3
 07da8000-07da9000 rw-p 00000000 00:00 0 
 08048000-08049000 r-xp 00000000 08:01 5509168    /usr/lib/jvm/java-7-oracle/jre/bin/java
 08049000-0804a000 rw-p 00000000 08:01 5509168    /usr/lib/jvm/java-7-oracle/jre/bin/java
 0830c000-08358000 r-xp 00000000 08:01 50364      /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
 08358000-08359000 r--p 0004b000 08:01 50364      /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
 08359000-0835a000 rw-p 0004c000 08:01 50364      /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
 084ff000-0851f000 r-xp 00000000 08:01 12857      /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 0851f000-08520000 r--p 0001f000 08:01 12857      /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 08520000-08521000 rw-p 00020000 08:01 12857      /usr/lib/i386-linux-gnu/libdrm_intel.so.1.0.0
 08565000-08a31000 rw-p 00000000 00:00 0          [heap]
 947fd000-94bfd000 rw-s 1ba68000 00:05 6584       /dev/dri/card0
 94bfd000-94ffe000 rw-p 00000000 00:00 0 
 94ffe000-950fe000 rw-s 1b8e1000 00:05 6584       /dev/dri/card0
 950fe000-951ff000 rw-p 00000000 00:00 0 
 951ff000-952ff000 rw-s 1b7e1000 00:05 6584       /dev/dri/card0
 952ff000-95400000 rw-p 00000000 00:00 0 
 95400000-95461000 rw-p 00000000 00:00 0 
 95461000-95500000 ---p 00000000 00:00 0 
 955fc000-955fd000 ---p 00000000 00:00 0 
 955fd000-95dfd000 rw-p 00000000 00:00 0 
 95dfd000-95dfe000 ---p 00000000 00:00 0 
 95dfe000-95efe000 rw-p 00000000 00:00 0 
 95efe000-99eff000 rw-s 00000000 00:12 134925     /run/shm/pulse-shm-2108405277
 99eff000-99f00000 ---p 00000000 00:00 0 
 99f00000-9a700000 rw-p 00000000 00:00 0 
 9a700000-9a7f9000 rw-p 00000000 00:00 0 
 9a7f9000-9a800000 ---p 00000000 00:00 0 
 9a84a000-9b14f000 rw-p 00000000 00:00 0 
 9b14f000-9b3b3000 rw-s 00000000 00:04 2260999    /SYSV00000000 (deleted)
 9b3b3000-9b7f1000 rw-p 00000000 00:00 0 
 9b800000-9b8e8000 rw-p 00000000 00:00 0 
 9b8e8000-9b900000 ---p 00000000 00:00 0 
 9b900000-9b9d1000 rw-p 00000000 00:00 0 
 9b9d1000-9ba00000 ---p 00000000 00:00 0 
 9ba00000-9baf4000 rw-p 00000000 00:00 0 
 9baf4000-9bb00000 ---p 00000000 00:00 0 
 9bb00000-9bbfb000 rw-p 00000000 00:00 0 
 9bbfb000-9bc00000 ---p 00000000 00:00 0 
 9bc00000-9bcf9000 rw-p 00000000 00:00 0 
 9bcf9000-9bd00000 ---p 00000000 00:00 0 
 9bd81000-9bf00000 rw-p 00000000 00:00 0 
 9bf00000-9bfcb000 rw-p 00000000 00:00 0 
 9bfcb000-9c000000 ---p 00000000 00:00 0 
 9c056000-9c059000 ---p 00000000 00:00 0 
 9c059000-9c0a7000 rw-p 00000000 00:00 0 
 9c0a7000-9c0aa000 ---p 00000000 00:00 0 
 9c0aa000-9c0f8000 rw-p 00000000 00:00 0 
 9c1ad000-9c1b0000 ---p 00000000 00:00 0 
 9c1b0000-9c1fe000 rw-p 00000000 00:00 0 
 9c1fe000-9c201000 ---p 00000000 00:00 0 
 9c201000-9c24f000 rw-p 00000000 00:00 0 
 9c24f000-9c252000 ---p 00000000 00:00 0 
 9c252000-9c2a0000 rw-p 00000000 00:00 0 
 9c2a0000-9c300000 rw-s 00000000 00:04 786436     /SYSV00000000 (deleted)
 9c300000-9c3f1000 rw-p 00000000 00:00 0 
 9c3f1000-9c400000 ---p 00000000 00:00 0 
 9c408000-9c40b000 ---p 00000000 00:00 0 
 9c40b000-9c459000 rw-p 00000000 00:00 0 
 9c459000-9c45c000 ---p 00000000 00:00 0 
 9c45c000-9c4aa000 rw-p 00000000 00:00 0 
 9c4aa000-9c4ad000 ---p 00000000 00:00 0 
 9c4ad000-9c4fb000 rw-p 00000000 00:00 0 
 9c4fb000-9c4fe000 ---p 00000000 00:00 0 
 9c4fe000-9c54c000 rw-p 00000000 00:00 0 
 9c54c000-9c54d000 ---p 00000000 00:00 0 
 9c54d000-9cd4d000 rw-p 00000000 00:00 0 
 9cd4d000-9cd6a000 r--p 00000000 08:01 250841     /usr/share/fonts/truetype/droid/DroidSansMono.ttf
 9cd6a000-9cdc1000 r--p 00000000 08:01 122665     /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
 9ce00000-9cef9000 rw-p 00000000 00:00 0 
 9cef9000-9cf00000 ---p 00000000 00:00 0 
 9cf00000-9cffe000 rw-p 00000000 00:00 0 
 9cffe000-9d000000 ---p 00000000 00:00 0 
 9d000000-9d0ff000 rw-p 00000000 00:00 0 
 9d0ff000-9d100000 ---p 00000000 00:00 0 
 9d179000-9d196000 r--s 00207000 00:14 5509049    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/tools.jar
 9d1f3000-9d1f4000 r--s 00000000 08:01 3461       /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
 9d1f4000-9d1fa000 r--s 00000000 08:01 3390       /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
 9d1fa000-9d1fc000 r--s 00000000 08:01 3451       /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
 9d1fc000-9d202000 r--s 00000000 08:01 3291       /var/cache/fontconfig/a6d8cf8e4ec09cdbc8633c31745a07dd-le32d4.cache-3
 9d202000-9d205000 r--s 00000000 08:01 3399       /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
 9d205000-9d206000 r--s 00000000 08:01 3380       /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
 9d206000-9d207000 r--s 00000000 08:01 3362       /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
 9d207000-9d20b000 r--s 00000000 08:01 3341       /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
 9d20b000-9d20e000 r--s 00000000 08:01 2871       /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
 9d20e000-9d219000 r--s 00000000 08:01 3252       /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-3
 9d219000-9d21c000 r--s 00000000 08:01 1699       /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-3
 9d21c000-9d21d000 r--s 00000000 08:01 4259       /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
 9d21d000-9d220000 r--s 00000000 08:01 1488       /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-3
 9d220000-9d242000 r--s 00000000 08:01 3244       /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
 9d242000-9d246000 r--s 00000000 08:01 3235       /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le32d4.cache-3
 9d246000-9d247000 r--s 00000000 08:01 3231       /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le32d4.cache-3
 9d247000-9d248000 r--s 00000000 08:01 3227       /var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le32d4.cache-3
 9d248000-9d24c000 r--s 00000000 08:01 3215       /var/cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le32d4.cache-3
 9d24c000-9d252000 r--s 00000000 08:01 3207       /var/cache/fontconfig/52f7bdb7ce746bfd7eaa1985bd9cfa93-le32d4.cache-3
 9d252000-9d25f000 r--s 00000000 08:01 3205       /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
 9d25f000-9d263000 r--s 00000000 08:01 3191       /var/cache/fontconfig/3f7329c5293ffd510edef78f73874cfd-le32d4.cache-3
 9d263000-9d26b000 r--s 00000000 08:01 3003       /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
 9d26b000-9d26e000 r--s 00000000 08:01 1994       /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
 9d26e000-9d273000 r--s 00000000 00:14 42952      /home/[username]/.fontconfig/4e93a9e49221ab1679435ee14ee5ffe6-le32d4.cache-3
 9d300000-9d3fc000 rw-p 00000000 00:00 0 
 9d3fc000-9d400000 ---p 00000000 00:00 0 
 9d42e000-9d43f000 rw-s 00000000 00:04 3538956    /SYSV00000000 (deleted)
 9d43f000-9d440000 ---p 00000000 00:00 0 
 9d440000-9dc40000 rw-p 00000000 00:00 0 
 9dc40000-9dc41000 ---p 00000000 00:00 0 
 9dc41000-9e441000 rw-p 00000000 00:00 0 
 9e441000-9e444000 ---p 00000000 00:00 0 
 9e444000-9e492000 rw-p 00000000 00:00 0 
 9e492000-9e495000 ---p 00000000 00:00 0 
 9e495000-9e4e3000 rw-p 00000000 00:00 0 
 9e4e3000-9e4e6000 ---p 00000000 00:00 0 
 9e4e6000-9e534000 rw-p 00000000 00:00 0 
 9e534000-9e537000 ---p 00000000 00:00 0 
 9e537000-9e585000 rw-p 00000000 00:00 0 
 9e585000-9e588000 ---p 00000000 00:00 0 
 9e588000-9e5d6000 rw-p 00000000 00:00 0 
 9e5d6000-9e5d9000 ---p 00000000 00:00 0 
 9e5d9000-9e627000 rw-p 00000000 00:00 0 
 9e627000-9e62a000 ---p 00000000 00:00 0 
 9e62a000-9e678000 rw-p 00000000 00:00 0 
 9e678000-9e67b000 ---p 00000000 00:00 0 
 9e67b000-9e6c9000 rw-p 00000000 00:00 0 
 9e6c9000-9e6cc000 ---p 00000000 00:00 0 
 9e6cc000-9e71a000 rw-p 00000000 00:00 0 
 9e71a000-9e71d000 ---p 00000000 00:00 0 
 9e71d000-9e76b000 rw-p 00000000 00:00 0 
 9e76b000-9e76e000 ---p 00000000 00:00 0 
 9e76e000-9e7bc000 rw-p 00000000 00:00 0 
 9e7bc000-9e7bf000 ---p 00000000 00:00 0 
 9e7bf000-9e80d000 rw-p 00000000 00:00 0 
 9e80d000-9e810000 ---p 00000000 00:00 0 
 9e810000-9e85e000 rw-p 00000000 00:00 0 
 9e85e000-9e861000 ---p 00000000 00:00 0 
 9e861000-9e8af000 rw-p 00000000 00:00 0 
 9e8af000-9e8b2000 ---p 00000000 00:00 0 
 9e8b2000-9e900000 rw-p 00000000 00:00 0 
 9e900000-9e9fc000 rw-p 00000000 00:00 0 
 9e9fc000-9ea00000 ---p 00000000 00:00 0 
 9ea08000-9ea0b000 ---p 00000000 00:00 0 
 9ea0b000-9ea59000 rw-p 00000000 00:00 0 
 9ea65000-9eae8000 rw-p 00000000 00:00 0 
 9eae8000-9eaeb000 ---p 00000000 00:00 0 
 9eaeb000-9eb39000 rw-p 00000000 00:00 0 
 9eb39000-9eb3a000 ---p 00000000 00:00 0 
 9eb3a000-9ebba000 rw-p 00000000 00:00 0 
 9ebba000-9ebbd000 ---p 00000000 00:00 0 
 9ebbd000-9ec0b000 rw-p 00000000 00:00 0 
 9ec0b000-9ec0e000 ---p 00000000 00:00 0 
 9ec0e000-9ec8c000 rw-p 00000000 00:00 0 
 9ec8c000-9ec8f000 ---p 00000000 00:00 0 
 9ec8f000-9ed0d000 rw-p 00000000 00:00 0 
 9ed0d000-9ed10000 ---p 00000000 00:00 0 
 9ed10000-9ed5e000 rw-p 00000000 00:00 0 
 9ed5e000-9ef5e000 r--p 00000000 08:01 43684      /usr/lib/locale/locale-archive
 9ef5e000-9ef61000 ---p 00000000 00:00 0 
 9ef61000-9efaf000 rw-p 00000000 00:00 0 
 9efaf000-9efb2000 ---p 00000000 00:00 0 
 9efb2000-9f000000 rw-p 00000000 00:00 0 
 9f000000-9f100000 rw-p 00000000 00:00 0 
 9f101000-9f10b000 r--s 00254000 08:01 5510685    /usr/lib/jvm/java-7-oracle/jre/lib/resources.jar
 9f10b000-9f112000 r--s 00000000 08:01 50915      /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
 9f112000-9f115000 ---p 00000000 00:00 0 
 9f115000-9f123000 rw-p 00000000 00:00 0 
 9f123000-9f2e0000 r--s 039da000 08:01 5510600    /usr/lib/jvm/java-7-oracle/jre/lib/rt.jar
 9f2e0000-a0000000 rw-p 00000000 00:00 0 
 a0000000-a0100000 rw-p 00000000 00:00 0 
 a0102000-a0103000 rw-s 190cc000 00:05 6584       /dev/dri/card0
 a0103000-a0107000 r--s 0002d000 08:01 5636169    /usr/lib/jvm/java-7-oracle/jre/lib/ext/sunjce_provider.jar
 a0109000-a010a000 rw-s 00000000 00:04 134939     /drm mm object (deleted)
 a010a000-a010b000 rw-s 190e3000 00:05 6584       /dev/dri/card0
 a010b000-a010d000 rw-s 00000000 00:04 135612     /drm mm object (deleted)
 a010d000-a0112000 r--s 0003d000 00:14 5509069    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/Inkubus.jar
 a011e000-a011f000 rw-p 00000000 00:00 0 
 a011f000-a0134000 r--s 001ed000 00:14 5509050    /home/[username]/.java/deployment/cache/lwjglcache/managerspiel.bundesliga.de/bundesliga_de/bundesliga.jar
 a0134000-a0135000 ---p 00000000 00:00 0 
 a0135000-a0200000 rw-p 00000000 00:00 0 
 a0200000-a02b4000 rw-p 00000000 00:00 0 
 a02b4000-a0300000 ---p 00000000 00:00 0 
 a0300000-a0301000 r--s 00003000 08:01 5636166    /usr/lib/jvm/java-7-oracle/jre/lib/ext/sunec.jar
 a0301000-a030a000 r--p 00000000 00:14 627        /home/[username]/.config/dconf/user
 a030a000-a0337000 r--p 00000000 08:01 18411      /usr/share/glib-2.0/schemas/gschemas.compiled
 a0337000-a0338000 ---p 00000000 00:00 0 
 a0338000-a03b8000 rw-p 00000000 00:00 0 
 a03b8000-a03b9000 ---p 00000000 00:00 0 
 a03b9000-a0451000 rw-p 00000000 00:00 0 
 a0451000-a048f000 rw-p 00000000 00:00 0 
 a048f000-a049c000 rw-p 00000000 00:00 0 
 a049c000-a04af000 rw-p 00000000 00:00 0 
 a04af000-a04c7000 rw-p 00000000 00:00 0 
 a04c7000-a0504000 rw-p 00000000 00:00 0 
 a0504000-a051c000 rw-p 00000000 00:00 0 
 a051c000-a051d000 ---p 00000000 00:00 0 
 a051d000-a052f000 rw-p 00000000 00:00 0 
 a052f000-a1db0000 rw-p 00000000 00:00 0 
 a1db0000-a4530000 rw-p 00000000 00:00 0 
 a4530000-a7370000 rw-p 00000000 00:00 0 
 a7370000-aefe0000 rw-p 00000000 00:00 0 
 aefe0000-b1d40000 rw-p 00000000 00:00 0 
 b1d40000-b1f70000 ---p 00000000 00:00 0 
 b1f70000-b4530000 rw-p 00000000 00:00 0 
 b4530000-b4532000 r--s 00019000 08:01 5510606    /usr/lib/jvm/java-7-oracle/jre/lib/jce.jar
 b4532000-b4534000 r--s 0000f000 00:14 4597148    /home/[username]/.java/deployment/cache/6.0/8/53d37d48-65149d99
 b4534000-b4538000 r--s 0008a000 08:01 5510716    /usr/lib/jvm/java-7-oracle/jre/lib/jsse.jar
 b4538000-b4541000 rw-p 00000000 00:00 0 
 b4541000-b45f8000 rw-p 00000000 00:00 0 
 b45f8000-b4838000 rwxp 00000000 00:00 0 
 b4838000-b75f8000 rw-p 00000000 00:00 0 
 b75f8000-b7600000 rw-s 00000000 08:01 17432623   /tmp/hsperfdata_[username]/13577
 b7600000-b76fa000 rw-p 00000000 00:00 0 
 b76fa000-b7700000 ---p 00000000 00:00 0 
 b7700000-b7701000 r--s 00000000 00:14 703        /home/[username]/.cache/dconf/user
 b7701000-b7713000 r--s 0019b000 08:01 5510719    /usr/lib/jvm/java-7-oracle/jre/lib/plugin.jar
 b7713000-b771c000 r--s 000d5000 08:01 5510723    /usr/lib/jvm/java-7-oracle/jre/lib/javaws.jar
 b771c000-b7729000 rw-p 00000000 00:00 0 
 b7729000-b773c000 rw-p 00000000 00:00 0 
 b773c000-b773f000 ---p 00000000 00:00 0 
 b773f000-b778f000 rw-p 00000000 00:00 0 
 b778f000-b7792000 r--s 000f7000 08:01 5636167    /usr/lib/jvm/java-7-oracle/jre/lib/ext/localedata.jar
 b7792000-b7793000 r--p 002c5000 08:01 43684      /usr/lib/locale/locale-archive
 b7793000-b77aa000 r--s 003bb000 08:01 5510726    /usr/lib/jvm/java-7-oracle/jre/lib/deploy.jar
 b77aa000-b77ab000 rw-p 00000000 00:00 0 
 b77ab000-b77ac000 r--p 00000000 00:00 0 
 b77ac000-b77ae000 rw-p 00000000 00:00 0 
 bfbb4000-bfbd5000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:	java
 State:	D (disk sleep)
 Tgid:	13577
 Pid:	13577
 PPid:	2586
 TracerPid:	0
 Uid:	1000	1000	1000	1000
 Gid:	1000	1000	1000	1000
 FDSize:	256
 Groups:	4 20 24 46 110 112 120 122 1000 
 VmPeak:	  667404 kB
 VmSize:	  610660 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	  119376 kB
 VmRSS:	  113948 kB
 VmData:	  497480 kB
 VmStk:	     136 kB
 VmExe:	       4 kB
 VmLib:	   37492 kB
 VmPTE:	     280 kB
 VmSwap:	       0 kB
 Threads:	38
 SigQ:	0/23969
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000004
 SigIgn:	0000000000001000
 SigCgt:	2000000181004ccf
 CapInh:	0000000000000000
 CapPrm:	0000000000000000
 CapEff:	0000000000000000
 CapBnd:	ffffffffffffffff
 Cpus_allowed:	3
 Cpus_allowed_list:	0-1
 Mems_allowed:	1
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	71
 nonvoluntary_ctxt_switches:	0
Signal: 6
Uname: Linux 3.2.0-38-generic i686
UserGroups: adm admin cdrom dialout lpadmin netdev plugdev sambashare
CoreDump: base64
```

---

### Post by jivana on 2013-02-26
Anyone?

---


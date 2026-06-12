---
title: "pcsx2 0.9.7 - wrong ELF class errors on startup - AMD64"
date: 2010-06-13
forum: Gaming &amp; Leisure
---

### Post by jonqrandom on 2010-06-13
i've installed the [[COLOR="Blue"]latest beta of pcsx2[/COLOR]]("http://pcsx2.net/downloads.php?p=publicbeta") on lucid64, and *should* have its dependencies satisfied - i've installed ia32-libs, [[COLOR="Blue"]ia32-libs-pcsx2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1110977&highlight=pcsx2"), and used [[COLOR="Blue"]getlibs[/COLOR]]("http://ubuntuforums.org/showthread.php?t=474790") to sort out the 32bit wxwindows libraries.

when i try to run it, it pops up a "warning: this a beta" notification, i click on OK, and it then sends the following to the console;

```
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
./pcsx2: relocation error: ./pcsx2: symbol _ZN12wxSizerFlags24ReserveSpaceEvenIfHiddenEv, version WXU_2.8.8 not defined in file libwx_gtk2u_core-2.8.so.0 with link time reference

```
[FONT="Courier New"]libgvfsdbus.so[/FONT] and [FONT="Courier New"]libgioremote-volume-monitor.so[/FONT] are from ia32-libs which i have installed. i'm just confused now :(

i'm guessing i need to make pcsx2 look in /usr/lib32/ for the libraries but i have no idea how. please help if you can, i'm out of my depth here. thank you :)

---

### Post by wingnux on 2010-07-07
Your best try (and recommended by the pcsx2 developers) is to run a 32bit chroot.

You can also look here for the needed libraries: [http://code.google.com/p/pcsx2/wiki/CompilationGuideForLinux](http://code.google.com/p/pcsx2/wiki/CompilationGuideForLinux)

> # 32 bits libraries on x86_64 (NOT SUPPORTED & IMCOMPLETE)

    * ia32-libs
    * ia32-libs-gtk
    * lib32asound2
    * lib32z1-dev 

---


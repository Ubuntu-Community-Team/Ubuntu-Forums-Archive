---
title: "Dofus 2.0 - Uplauncher Dofus 2.0 is already running"
date: 2010-01-21
forum: Gaming &amp; Leisure
---

### Post by frecel on 2010-01-21
I cant get Dofus 2.0 to run on my Ubuntu 9.10 64-bit. After I start the Uplauncher an error message pops-up  saying "Uplauncher Dofus 2.0 is already running. It cannot be launched more than once." but there is no other uplauncher running. I chcecked in the system monitor and restarted the system to be sure.

Here is what comes up in terminal
```
frecel@frecel-desktop:~$ /home/frecel/ankama/Dofus/share/UpLauncher
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
```

Installation and update went without any problems. My adobe air is running perfectly fine (I used 32-bit libs to make it work), I have another program that uses air and it works great.

Please help, I really want to play the new version of Dofus.

---

### Post by kvarley on 2010-07-09
Have you tried running Dofus as sudo?

The updater most likely is trying to write changes to directories which require root permissions to write data.

---


---
title: "unreal tournament GOTY what files to copy"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by unixguru on 2007-04-25
I tried installing it with the installer but it just won't detect my cdrom and keeps asking to mount the cd so i just installed the binary files. Now can some one tell me which files to copy from cd1 and cd2 to make it work.

---

### Post by aidanr on 2007-04-25
that won't quite work because the maps (and i think maybe the textures) are compressed and are uncompressed during the install

have a read through [this]("http://ubuntuforums.org/showthread.php?t=289796&highlight=ut+goty") thread, personally i just installed via wine, and then ran the loki installer installing the binaries only and them copied the stuff from the wine install

---

### Post by unixguru on 2007-04-25
Can you tell me exactly what files to copy from the windows install?

---

### Post by aidanr on 2007-04-26
just copy them all over and don't overwrite anything

---

### Post by unixguru on 2007-04-26
I am getting this after copying everythin from windows install, i did not replace any file in System directory of ut
```

Unreal engine initialized
Failed to load 'WinDrv': Can't find file for package 'WinDrv'
Failed to load 'Class WinDrv.WindowsClient': Can't find file for package 'WinDrv'
Can't find file for package 'WinDrv'
appError called:
Can't find file for package 'WinDrv'
Executing UObject::StaticShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down


```

---

### Post by unixguru on 2007-04-26
Ok, i think i got it right. I copied only the *.u files from windows install System folder. Everything seems to be working fine now.

---


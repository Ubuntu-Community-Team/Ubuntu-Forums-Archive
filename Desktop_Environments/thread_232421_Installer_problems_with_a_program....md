---
title: "Installer problems with a program..."
date: 2006-08-08
forum: Desktop Environments
---

### Post by smiley2billion on 2006-08-08
This may not be able to be answered here but I was having some problems with a certain applications installer.

The application is from a company called Navini, they make wireless network equipment.  The link to the program is here:

[http://navini.com/Website/assets/downloads/support/navdiag_linux.bin]("http://navini.com/Website/assets/downloads/support/navdiag_linux.bin")

The installer is spitting this out at me:
```
~/sudo sh navdiag_linux.bin
Preparing to install...

Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Error occurred during initialization of VM
Unable to load native library: /tmp/install.dir.7649/Linux/resource/jre/lib/i386/libjava.so: symbol __libc_wait, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```

My best guess is that it's not properly linking to the correct (newer) "libc.so.6" files, as indicated by the "not defined" error.  I really have no idea how to fix this. I have tried to link different libraries and what not, but it's not having any of it.  If someone could get this bin file and  get it to install/run it would be wonderful, as this is mission critical software for us and we're trying to stay away from switching back to Windows just for this software whereas they offer a Linux version but we just can't use it.

---

### Post by jordilin on 2006-08-08
> Error occurred during initialization of VM
I think it's something related to the java virtual machine. What java vm do you have, the one provided by Sun?

---

### Post by smiley2billion on 2006-08-11
Yes, I have JVM 1.5 installed from Sun.

An example website that works that uses Java is this:

[http://nuvisionsbroadband.com/support/Speedtest/index.html](http://nuvisionsbroadband.com/support/Speedtest/index.html)

---


---
title: "vmware player installation/configuration problems"
date: 2006-06-20
forum: Desktop Environments
---

### Post by mm144 on 2006-06-20
i didn't know where this should go so i decided on general.

In the ubuntu 6.06 betas i've had no trouble but since i reformatted and put the release on my computer i can't get vmware player to configure properly.
before i run the installation, i did the auto update and installed make, the headers and gcc 4

when i ran the installer (vmware-install.pl) i selected all the defaults except when it asked about gcc(which it couldn't find) i gave the binary location of:/usr/bin/gcc-4.0

now after this i get:
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.15-25-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
/usr/src/linux-headers-2.6.15-25-386/scripts/gcc-version.sh: line 11: gcc: comma nd not found
/usr/src/linux-headers-2.6.15-25-386/scripts/gcc-version.sh: line 12: gcc: comma nd not found
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-386'
make[2]: gcc: Command not found
/tmp/vmware-config0/vmmon-only/Makefile:89: *** Inappropriate build environment:  you wanted to use gcc version 4.0.3 while kernel attempts to use gcc version .
/tmp/vmware-config0/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc with symbolic link to /usr/bin/gcc-4.0.  Stop.
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

i can't figure out why it refuses to work. 
any help would be greatly appriciated

---

### Post by mm144 on 2006-06-20
i feel like an idiot.... i figured it out.... rename gc-4.0 to gcc and tadda it worked.

---

### Post by kupajava on 2006-06-20
[QUOTE=mm144]i feel like an idiot.... i figured it out.... rename gc-4.0 to gcc and tadda it worked.[/QUOTE]

Dont feel bad, Im a bigger idiot I guess, because I have the same problem and need to know where exactly I need to go to rename that file.  Could you be a little more specific in this resolution so I can do it too?

---

### Post by lamego on 2006-06-20
Renameming gcc-4.0 to gcc is a bad practice and may break your system in the future.
If you have gcc4 installed you should have a gcc which is a link to it, if you don't have then your install is broken, remove it and install it again.

About vmware player it is available on the ubuntu multiverse repositories, just make sure they are added and:
  sudo apt-get install vmware-player

---

### Post by snellgrove on 2006-07-01
Is this one of those kernel compiled with GCC version X, and now an update has installed GCC version Y, which it is now using and thus wont work?

If so, I believe theres some command like "Export CC=" and then the GCC version or something, and then running the config script and it should work?

Have to wait for more of an expert to reply though, with the answer.

---


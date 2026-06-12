---
title: "VMware wants 2.6.12-10-386 kernel headers"
date: 2006-07-29
forum: Desktop Environments
---

### Post by jonathanhayward on 2006-07-29
I just tried to upgrade from Breezie Badger to Dapper Drake. VMware is complaining that it doesn't have kernel sources, and when I try "aptitude install kernel-source" it says "Note: selecting "kernel-source-2.4.27" instead of the virtual package "kernel-source"" and installs the other sources.

When I run vmware-config.pl, I get:

root@inner-sanctum:~# vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

***
* Updating MIME database in /usr/share/mime...
Wrote 481 strings at 20 - 2818
Wrote aliases at 2818 - 29c4
Wrote parents at 29c4 - 3374
Wrote literal globs at 3374 - 33d0
Wrote suffix globs at 33d0 - 67a8
Wrote full globs at 67a8 - 67cc
Wrote magic at 67cc - bfe4
Wrote namespace list at bfe4 - bff4
***
In which directory do you want to install the mime type icons?
[/usr/share/icons]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The directory of kernel headers (version 2.6.12-10-386) does not match your
running kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /lib/modules/2.6.12-10-386

The path "/lib/modules/2.6.12-10-386" is an existing directory, but it does not
contain at least one of these directories "linux", "asm", "net" as expected.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

**How do I download the 2.6.12-10-386 C kernel header files so that vmware will recognize them? I'd like to have vmware up and running again and this is a major loss of functionality to not have vmware running.**

---

### Post by jonathanhayward on 2006-07-29
P.S. On my system, I have the headers for 2.6.12-**10** while vmware specifically thinks it needs 2.6.12-**26**:

From the command line:

jonathan@inner-sanctum:/usr/src$ ls
kernel-source-2.4.27.tar.bz2  linux-headers-2.6.12-10-386  rpm
linux                         linux-headers-2.6.12-9
linux-headers-2.6.12-10       linux-headers-2.6.12-9-386

From vmware-config.pl:

... What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-10-386/include/

The directory of kernel headers (version 2.6.12-10-386) does not match your
running kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux/include

The directory of kernel headers (version 2.6.12-10-386) does not match your
running kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

---

### Post by jonathanhayward on 2006-07-29
Correction: vmware wants **2.6.15-26**, not 2.6.**12**-26 as incorrectly stated in my earlier post.

Where can I download kernel headers that vmware will recognize as being the same as the installed kernel?

---

### Post by Dubbayoo on 2006-07-29
I think you need to run apt-get update because I see those liste in synaptic.

---

### Post by jonathanhayward on 2006-07-29
[INDENT]I think you need to run apt-get update because I see those liste in synaptic.[/INDENT]

I ran something like apt-get install kernel-source and this time got linux-source-2.6.15.tar.bz2 

BUT

[INDENT]What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-source-2.6.15/include

The directory of kernel headers (version 2.6.15.7-ubuntu1) does not match your
running kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include][/INDENT]

This is detected as a different version. How can I get the **exact same version** of kernel header files as my computer was upgraded to?

---

### Post by moma on 2006-07-29
Your current, running kernel is 
$ uname -r
------
$ sudo apt-get update 

$ sudo aptitude install linux-headers-$(uname -r)

$ sudo aptitude install linux-headers-$(uname -r | sed 's/-[3-6]86$//')

Use --reinstall option if you must.

---

### Post by jonathanhayward on 2006-07-29
[INDENT]$ sudo aptitude install linux-headers-$(uname -r)[/INDENT]

Thank you; that's just what I needed.

---


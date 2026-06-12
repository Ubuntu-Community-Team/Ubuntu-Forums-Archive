---
title: "linux headers"
date: 2005-12-26
forum: General Help
---

### Post by cached on 2005-12-26
I am trying to install VMWare, but I do not have the correct headers.

> What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-10-386/include

The path "/usr/src/linux-headers-2.6.12-10-386/include" is not an existing
directory.

So I try to get it off of apt-get using "sudo apt-get install linux-headers-$(uname -r)"

but that gives me 
> cached@Shadow:/usr$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-10-386

I tried, just to see if it would work, to copy the 2.6.12-9 folder I had and renaming it to 2.6.12-10, but that did not work out.

> 
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-10-386/include

The directory of kernel headers (version 2.6.12-9-386) does not match your
running kernel (version 2.6.12-10-386).  Even if the module were to compile
successfully, it would not load into the running kernel.


Any ideas?

---

### Post by gsdefender on 2005-12-26
If kernel sources are already installed, try this (as root):

         ln -s /usr/src/linux/include /usr/include/linux
         ln -s /usr/src/linux/asm-generic /usr/include/asm-generic
         ln -s /usr/src/linux/include/asm-i386 /usr/include/asm-i386 
        ln -s /usr/include/asm-i386 /usr/include/asm

Don't forget to do a 

             make dep

before trying to install VMWare.

---

### Post by cached on 2005-12-26
> 
Don't forget to do a 

             make depend.

before trying to install VMWare.

How?

---

### Post by gsdefender on 2005-12-26
I just forgot that Ubuntu is using a 2.6 kernel ;-):

Do
make oldconfig; make

and halt the process when you see the first line containing

gcc

then retry installing VMWare.

---

### Post by cached on 2005-12-26
[QUOTE=gsdefender]I just forgot that Ubuntu is using a 2.6 kernel ;-):

Do
make oldconfig; make

and halt the process when you see the first line containing

gcc

then retry installing VMWare.[/QUOTE]
cached@Shadow:~$ make oldconfig; make
make: *** No rule to make target `oldconfig'.  Stop.
make: *** No targets specified and no makefile found.  Stop.

---

### Post by gsdefender on 2005-12-26
I don't have my Ubuntu handy right now. Try to do that (as root):

ls /boot/config*

If a file matching your kernel version appears, do

cp /boot/[filename] /usr/src/linux/.config; cd /usr/src/linux; make oldconfig; make

---

### Post by kaamos on 2005-12-26
[QUOTE=cached]cached@Shadow:/usr$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-10-386[/QUOTE]
I thought this didn't look right..
```
alaisi@ubuntu:~$ apt-cache show linux-headers-2.6.12-10-386
Package: linux-headers-2.6.12-10-386
Priority: optional
Section: devel
Installed-Size: 21260
Maintainer: Ben Collins <ben.collins@ubuntu.com>
Architecture: i386
Source: linux-source-2.6.12
Version: 2.6.12-10.25
Provides: linux-headers, linux-headers-2.6
Depends: coreutils | fileutils (>= 4.0), linux-headers-2.6.12-10, libc6 (>= 2.3.4-1)
Filename: pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10-386_2.6.12-10.25_i386.deb
Size: 801032
MD5sum: c819c2b635c2fe4cc93720afde56fc9c
Description: Linux kernel headers 2.6.12 on 386
 This package provides kernel header files for version 2.6.12 on
 386,
 for sites that want the latest kernel headers.
 Please read /usr/share/doc/linux-headers-2.6.12-10/debian.README.gz for
 details
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by cached on 2005-12-26
[QUOTE=kaamos]I thought this didn't look right..
```
alaisi@ubuntu:~$ apt-cache show linux-headers-2.6.12-10-386
Package: linux-headers-2.6.12-10-386
Priority: optional
Section: devel
Installed-Size: 21260
Maintainer: Ben Collins <ben.collins@ubuntu.com>
Architecture: i386
Source: linux-source-2.6.12
Version: 2.6.12-10.25
Provides: linux-headers, linux-headers-2.6
Depends: coreutils | fileutils (>= 4.0), linux-headers-2.6.12-10, libc6 (>= 2.3.4-1)
Filename: pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10-386_2.6.12-10.25_i386.deb
Size: 801032
MD5sum: c819c2b635c2fe4cc93720afde56fc9c
Description: Linux kernel headers 2.6.12 on 386
 This package provides kernel header files for version 2.6.12 on
 386,
 for sites that want the latest kernel headers.
 Please read /usr/share/doc/linux-headers-2.6.12-10/debian.README.gz for
 details
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```[/QUOTE]

That doesn't show up for me.  I thought I have all repositories set up... hmmmm...

Thanks for the help so far, though :)

EDIT: Got it to work! Thanks!

---


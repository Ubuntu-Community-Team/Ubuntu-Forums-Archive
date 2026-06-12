---
title: "can't find kernel headers.."
date: 2006-08-18
forum: Desktop Environments
---

### Post by frup on 2006-08-18
I'm trying to re-install vmware server after a format and i'm running vmware-install.pl and its got to the part where it says 

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


i press enter and it says dir doesnt exist... which is true.. i downloaded the linux headers from synaptic... linux-headers-2.6.1-26 and the -386 and then tried again.. that didnt work... they were in the /usr/src folder...so i made /usr/src/linux/include and copied them there... thats didnt work... so i renamed the folders to linux and tried them one at a time and that didnt work... i then tried usr/include/linux and that didnt work and i came here...  please help :(


```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/

The path "/usr/src" is an existing directory, but it does not contain a "linux"
subdirectory as expected.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is an existing directory, but it does not
contain a "linux" subdirectory as expected.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is a kernel header file directory, but it
does not contain the file "linux/version.h" as expected.  This can happen if
the kernel has never been built, or if you have invoked the "make mrproper"
command in your kernel directory.  In any case, you may want to rebuild your
kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is a kernel header file directory, but it
does not contain the file "linux/version.h" as expected.  This can happen if
the kernel has never been built, or if you have invoked the "make mrproper"
command in your kernel directory.  In any case, you may want to rebuild your
kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is a kernel header file directory, but it
does not contain the file "linux/version.h" as expected.  This can happen if
the kernel has never been built, or if you have invoked the "make mrproper"
command in your kernel directory.  In any case, you may want to rebuild your
kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] usr/include

The path "usr/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/include

The header files in /usr/include are generally for C libraries, not for the
running kernel. If you do not have kernel header files in your /usr/src
directory, you probably do not have the kernel-source package installed. Are
you sure that /usr/include contains the header files associated with your
running kernel? [no]

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is an existing directory, but it does not
contain a "linux" subdirectory as expected.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] laurent@ubuntu:~/Desktop/vmware-server-distrib$
laurent@ubuntu:~/Desktop/vmware-server-distrib$

```

---

### Post by stinerman on 2006-08-18
Debian-based distros like Ubuntu don't put the kernel headers in the standard location.  Your headers will be somewhere like "/usr/src/linux-headers-2.6.15/", not "/usr/src/linux/"

---

### Post by frup on 2006-08-19
hey thanks... i figured that when i found them in usr/src only... but i think because i had already run the script when i got them off synaptic it couldnt read them properlly... 

i just re-ran the script and it automatically found them :S

so fingers crossed...  :)

---

### Post by Mennisco on 2006-08-20
I am having the same problem, all I can find in /usr/src is the following package:

/usr/src/linux-source-2.6.15.tar.bz2

How do I unpack this, so that the VMWare installer can find the kernel headers, or is this what I need to do?  :confused:

---

### Post by lupine_nickt on 2006-08-20
To install the correct linux headers for your kernel, run ```
apt-get install linux-headers-`uname -r`
```

As for the VMware installer, it's a complete PITA. Try using /lib/modules/(kernel version - given by uname -r)/build and see if it'll take that. If not, then /usr/src/linux-`uname -r` might be it.

If not, then I believe there's a patch for it somewhere - but I don't know where :(. I had to use it to get it running on OpenSUSE.

xF,

...Nick

---

### Post by lupine_nickt on 2006-08-20
Oh, and a quick note - the *correct* use of the /usr/src/linux symlink is to point to your *library* headers, not your kernel headers. Not that anyone cares ;)

xF,

...Nick

---

### Post by Mennisco on 2006-08-20
Thanks Nick! You da man!!:KS :)

---


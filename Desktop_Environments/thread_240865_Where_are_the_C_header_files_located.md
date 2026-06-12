---
title: "Where are the C header files located ?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by metalsam on 2006-08-21
Im follwoing the howto for installin VMware server, and the installer is asking me where the C header file for my kernel (Ubuntu 6.06) is located.

Anyone know ?

---

### Post by GoldBuggie on 2006-08-21
/usr/include/

---

### Post by Chris Tucker on 2006-08-21
You need to: ```
sudo apt-get install linux-headers-`uname -r`
```
The `uname -r` spawns an application outside apt-get that will identify your kernal, and dump it in the place of where you put the command. so the right linux headers for your kernel will be downloaded.

---

### Post by metalsam on 2006-08-21
thanks guys :)

---

### Post by lupine_nickt on 2006-08-21
The kernel header files are *not* in /usr/include (those are the C library headers!); once the linux-headers package has been installed, you'll find the  linux headers at /usr/src/linux-headers-`uname -r`

xF,

...Nick

---

### Post by GoldBuggie on 2006-08-21
oops...missed the kernel part of that sentance..sorry ...thought it was the header files for C. my mistake...:(

---

### Post by Giggity on 2006-08-21
I ran the "sudo apt-get install linux-headers-`uname -r`" and it installed everything with no errors, but:
```
The path "/usr/src/linux-headers-2.6.15-26" is an existing directory, but it
does not contain a "linux" subdirectory as expected.
```
What gives?

---

### Post by Giggity on 2006-08-21
Turns out I have two directories of headers, but neither satisfies the install script:
```
The path "/usr/src/linux-headers-2.6.15-26-386" is an existing directory, but
it does not contain a "linux" subdirectory as expected.
```
This is making me sad.  Should I just sudo rename one of these directories to "linux"?  Or would that damage something else on the machine?

---

### Post by xtknight on 2006-08-21
sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux

Then tell VMware /usr/src.

---

### Post by Giggity on 2006-08-21
Well, here's *some* progress.  At least it's giving me something different.
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src

The path "/usr/src" is a kernel header file directory, but it does not contain
the file "linux/version.h" as expected.  This can happen if the kernel has
never been built, or if you have invoked the "make mrproper" command in your
kernel directory.  In any case, you may want to rebuild your kernel.
```
Rebuild my kernel?  Jeez, I thought the attraction of these prepackaged distros was not having to do stuff like this!

---

### Post by Giggity on 2006-08-21
[This post]("http://www.ubuntuforums.org/showthread.php?t=239232") helped me past the last problem

---

### Post by coastdweller on 2006-08-22
Hi, I had the same problem.

I eventually browsed via konsole to /usr/src and noticed the names of the header "folders"

Try:

/usr/src/linux-headers-2.6.15-26-386/include

(Or whatever kernel you're running).

I was tired the other night trying this and decided to just suspend the vmware until I was better rested. Well finally worked.

Good luck :)

---

### Post by cbeaudin on 2006-08-24
I am having the same problem at the same point in installation. I also noticed that in the directory /usr/src/ none of the folders match the running kernel. When i run "sudo apt-get install linux-headers-`uname -r`"
 it comes up with the error:

E: Couldn't find package linux-headers-2.6.15-26-amd64-generic

The two folders in /usr/src/ are:
linux-headers-2.6.15-23
linux-headers-2.6.15-23-amd64-generic

Does anyone know why i cant update the headers?

---

### Post by mattc1973 on 2008-02-19
hello

know this thread was a long time ago but I've got exactly this same problem!

Anyone find a way round it?

cheers

---


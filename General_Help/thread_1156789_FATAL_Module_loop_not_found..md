---
title: "FATAL: Module loop not found."
date: 2009-05-12
forum: General Help
---

### Post by uglendertog on 2009-05-12
Hi 
I have just installed the base system of ubuntu 9 and then openbox. I was trying to mount an iso file when I ran into trouble. The loop module does not appear to working and I can't find the problem.

This is the error i'm getting

anders@anders:/dev$ sudo modprobe loop
FATAL: Module loop not found.

Can anyone help me?

-Anders

---

### Post by Lampi on 2009-05-12
hi anders - you are missing package loop-aes-modules

---

### Post by uglendertog on 2009-05-12
hey

I can't find loop-aes-modules in the repo but I have installed:

loop-aes-source
loop-aes-testsuite
loop-aes-utils

---

### Post by Lampi on 2009-05-12
agreed - in debian they ship this module along with the official kernel, that's why I was guessing wrong - so: you'd have to build this module using module-assistant and loop-aes-source

For me this failed with lot's of errors - there is allready a bug report about this on [Launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/loop-aes-source/+bug/362396") concerning jaunty 64bit edition - looks like it also concerns 32bit edition :(

---

### Post by Lampi on 2009-05-12
I just had a quick look at my intrepid installation and: this should be part of linux-image-2.6.28-11-generic. Apparently it is not.

[http://packages.ubuntu.com]("http://packages.ubuntu.com/search?searchon=contents&keywords=loop.ko&mode=&suite=jaunty&arch=i386") shows it in linux-image-2.6.28-6-386. I guess you don't want to go back there.

This is kind of strange ... sorry can't help you there

---

### Post by lex1 on 2009-05-20
yes your correct its not there.
THATS WHY ubuntu is a gret DISTRO but its NOT rock soild like debian etch or lenny.:popcorn:

---

### Post by mcduck on 2009-05-20
You don't need to "modprobe loop" in 9.04, the loopback driver is compiled into the kernel, not as a module.

---

### Post by trashie on 2009-07-09
And that's the problem !! We cannot anymore "modprobe" loop from loop-aes in 2.6.28 kernels, since we cannot "rmmod" the "normal" loop.

This is a big issue to me.

---


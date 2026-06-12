---
title: "question about compling a kernel."
date: 2009-05-13
forum: General Help
---

### Post by banana jama on 2009-05-13
im  using a hp pavilion dv6000 and my microphone doesn't work so im thinking about compling my own kernel from scratch. i've been reading the how from the following website 
[http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

it says to add hardware support to add do this: 
```
bzip2 -dc /usr/src/patch.bz2 | patch -p1 --dry-run
bzip2 -dc /usr/src/patch.bz2 | patch -p1
```

so my question is if i download the audio/mic drivers from hp website do i just replace patch.bz2 with the name of the file? in this case 	
sp37732.exe also can the file be in an .exe format because thats all that is on the hp website.

---

### Post by eldragon on 2009-05-13
if you are asking these type of questions, id advice you start fiddling with a non production machine, nothing against trying to learn, but you will most likely bork your install...

now on subject.

a patch is intendend against a certain kernel branch and a even a certain kernel version. and a patch should come from someone which modified the kernel (or a driver) and produced the patch from it. so you will most likely not find patches in the hp website.

again, if you want to add support for new hardware to your kernel, you dont need to compile the entire kernel, just find the appropiate source for your hardware's driver, and build that against the kernel headers / source. instructions to do that vary from driver to driver...

good luck

---

### Post by HermanAB on 2009-05-13
Howdy,

It is very easy.

Start by downloading the source for your current installed version and compile it without making any changes.  Install it and make sure it works.  Only then you start to experiment.

[http://aeronetworks.ca/kernel-compile-howto.html](http://aeronetworks.ca/kernel-compile-howto.html)

---

### Post by banana jama on 2009-05-13
at eldragon: lol i'll probably will and since this is my only computer im going to hold off of compling from stractch.

i've been looking at the website that herman posted and i think im going to try this way instead. hopefully it goes well thanks for the info.

---


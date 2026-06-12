---
title: "How to get source code"
date: 2009-03-13
forum: General Help
---

### Post by pgmer6809 on 2009-03-13
I am having a problem with the skge ethernet driver for the marvell chip.
At least I think it is with the driver.
How do I get the source code for this module from the Ubuntu repositories?
I would like to see if I can fix it.
According to the GPL it should be plain to me how to get it, but using SYNAPTICS search function does not give me any starting point.

Do I have to DL the whole kernel? if so from where?

Thanks,
pgmer6809

---

### Post by infinitejones on 2009-03-13
The way I understand it, the repositories aren't the place where you get source code. The repositories contain compiled packages (debs) and for installing software, that's what the majority of users would want, the majority of the time. 

The point of source code is that it isn't compiled, therefore it doesn't (usually) go in the repositories.

On the few occasions when I've needed to compile something from source, I've normally just used google, seaching for "[package name] source code" or something.

Having said that, when I googled "skge source code" I didn't find much apart from a load of bugs, error messages etc related to compiling skge from source - however that sounds like the subject of a completely different thread...

---

### Post by heindsight on 2009-03-13
For that you'll have to download the entire kernel source.

You can get a good explanation of how to get the source here: [uhelp]Kernel/Compile[/uhelp]

---

### Post by lloyd_b on 2009-03-13
Actually, the repositories *are* the correct place.```
apt-get source <package>
``` will retrieve the source code for any package in the repositories (with the possible exception of some restricted drivers - not sure about them).

You may need to uncomment some "deb-src" lines in the file "/etc/apt/sources.list" for this to work.

As for that particular driver: If it's part of the standard install, then it's almost certainly part of the kernel package, and as such you *will* need to get the entire kernel sources to get it from the repos.```
apt-get source linux-image-2.6.27-11-generic
``` will fetch the kernel sources (assuming you're running kernel 2.6.27-11, that is).

Lloyd B.

---

### Post by pgmer6809 on 2009-03-14
> **lloyd_b said:**
> Actually, the repositories *are* the correct place.```
apt-get source <package>
``` will retrieve the source code for any package in the repositories (with the possible exception of some restricted drivers - not sure about them).

You may need to uncomment some "deb-src" lines in the file "/etc/apt/sources.list" for this to work.

As for that particular driver: If it's part of the standard install, then it's almost certainly part of the kernel package, and as such you *will* need to get the entire kernel sources to get it from the repos.```
apt-get source linux-image-2.6.27-11-generic
``` will fetch the kernel sources (assuming you're running kernel 2.6.27-11, that is).

Lloyd B.

Thanks a lot Lloyd that is exactly what I needed. I knew the repos had source, but not how to figure out which package I needed.
Dl'ing 60mb of source as I type this.... ;)
pgmer6809

---


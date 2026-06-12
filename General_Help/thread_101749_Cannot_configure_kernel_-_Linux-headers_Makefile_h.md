---
title: "Cannot configure kernel - Linux-headers Makefile hard-linked to itself!"
date: 2005-12-10
forum: General Help
---

### Post by Fisslefink on 2005-12-10
I upgraded to Kubuntu Breezy 5.10 from Kubuntu Hoary using apt-get.  Afterwards, I used apt-get to switch to the x686 kernel (2.6.12-10-686).  Now I am trying to follow the [instructions for fglrx driver installation]("http://ubuntuforums.org/showthread.php?p=423584") and I encounter the error "Warning, /usr/src/linux-source-2.6.12 seems to contain unconfigured kernel source!" when I run "module-assistant prepare".  

So now I am trying to configure the kernel source, but "make prepare" returns the following:
```
fisslefink@kubuntubox:/usr/src/linux$ sudo make prepare
Password:
make: Makefile: No such file or directory
make: *** No rule to make target `Makefile'.  Stop.
```

Curious, I looked for Makefile, and it seems to be hard linked to itself!  See the output below:
```

fisslefink@kubuntubox:/usr/src/linux-headers-2.6.12-10-686$ pwd
/usr/src/linux-headers-2.6.12-10-686
fisslefink@kubuntubox:/usr/src/linux-headers-2.6.12-10-686$ ls -l Makefile
lrwxrwxrwx  1 root root 35 2005-12-09 21:33 Makefile -> ../linux-headers-2.6.12-10/Makefile
```

This could not be right, but I have no idea how to fix it.

Could someone please tell me, what does a good, working /usr/linux/src/Makefile look like? If it is a link, where is it pointing?  

Also, perhaps the kubuntu kernel source maintainers should take a look at the apt package, because this configuration problem is definitely not due to me mucking around.  Anyone know how to alert them?

Thanks.

Fisslefink

---

### Post by mlomker on 2005-12-11
First of all, the video driver doesn't require kernel source at all.  Perhaps you could post the exact error from  module-assistant?  Module-assistant should just downloads the headers and not the source.

I've also never configured a kernel the way that you are doing it.  Have you tried [this approach]("http://ubuntuforums.org/showthread.php?t=85064")?

---


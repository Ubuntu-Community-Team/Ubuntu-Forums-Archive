---
title: "Madwifi + kernel update"
date: 2007-09-03
forum: Debian
---

### Post by arijarot on 2007-09-03
I just switched from ubuntu to debian. I installed debian, installed/setup madwifi ([http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)) and then updated the system, which had a kernel update... After kernel update, wifi didn't work again, so I repeated the setup with the new kernel and it works fine now... But, synaptic is prompting me to update from installed version 2.6.18.dfsg.1-13 to "latest" version 2.6.18.dfsg.1-13etch2. Is this just the same/original (or as the terminal said un"tainted") kernel before I added madwifi or are these genuine updates that I need? Will a new kernel update break madwifi everytime?

---

### Post by shae on 2007-09-08
Yes everytime you update the kernel, you will have to recompile madwifi.  However, useing module assistant makes that process simple.

Personally I run a custom kernel, thus I am in control of kernel updates.  Using module assistant + custom kernel is great because whenever I build the kernel, it compiles the module packages for me (fglrx and madwifi)

You do not have to do the entire process however.  You only need to run something like this:
```

sudo -s
rm /usr/src/madwifi-modules-*_*+*_*.deb
m-a prepare
m-a update
m-a build madwifi
m-a install madwifi
exit

```

If you find you are updating the kernel alot (such as if you are using testing or unstable) you might want to create a script to do that for you.  With a little work, kernel updates will become no problem!  (Plus bad updates won't break things *cough cough* ubuntu)

---

### Post by arijarot on 2007-09-08
> **shae said:**
> Yes everytime you update the kernel, you will have to recompile madwifi.  However, useing module assistant makes that process simple.

Personally I run a custom kernel, thus I am in control of kernel updates.  Using module assistant + custom kernel is great because whenever I build the kernel, it compiles the module packages for me (fglrx and madwifi)

You do not have to do the entire process however.  You only need to run something like this:
```

sudo -s
rm madwifi-modules-*_*+*_*.deb
m-a prepare
m-a update
m-a build madwifi
m-a install madwifi
exit

```

If you find you are updating the kernel alot (such as if you are using testing or unstable) you might want to create a script to do that for you.  With a little work, kernel updates will become no problem!  (Plus bad updates won't break things *cough cough* ubuntu)

Thanks for the info. Recompiling madwifi is not so bad (just run ```
m-a prepare
``` then ```
m-a a-i madwifi
```), that's all. it's just pesky. 
Cheers:)

---


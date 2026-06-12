---
title: "Compiling Kernel 2.6.17.7 no devfs???"
date: 2006-08-07
forum: Desktop Environments
---

### Post by KamakazieX on 2006-08-07
Ive compiled the kernel 2 different ways with make clean/modules/install and make-kpkg. I get the same error every time I compile/install the kernel.

Says it does not understand/recognize devfs. Anyone know whats going on?

Thanks in advance,
Matt

---

### Post by xenblend on 2006-08-09
I'm getting teh same error.  I also tried both methods, the standard "make modules_install insall" and make-kpkg/dpkg methods for kernel 2.6.17.7.  Is it a bug?  What are you running?  I've got an Athlon XP 2600+ w/ 512 MB RAM, IDE drives, compiled-in ext2 and ext3 support.  I dont know what else might be relevent.  There is surprisingly little information out there regarding this topic.

If anyone has any ideas/suggestions, please help!

XB

---

### Post by xenblend on 2006-08-09
Hmm, a little more info...

At boot, the initial boot commands are loaded from menu.lst.  Both with and without initrd loading, the error: devfsd: No devfs in /dev, cannot mount" shows up right after "boot".  

Later in teh sequence, another error: "no devices in /etc/default/udftools" shows up.  These are the only errors I get at all in what seems to be an otherwise beautiful compilation (took me several days so it should be! :\)

Please help!

XB:confused:

---

### Post by MacMan on 2006-08-09
> **KamakazieX said:**
> Ive compiled the kernel 2 different ways with make clean/modules/install and make-kpkg. I get the same error every time I compile/install the kernel.

Says it does not understand/recognize devfs. Anyone know whats going on?


If I understand correctly what you've done, it seems to me you didn't configure the kernel first. That could be the reason for your problem. That's what I'd do.

cd into the kernel sources dir and then:
```

cp .config $HOME
make mrproper
cp /boot/config-$(uname -r) .
make oldconfig

```

This will backup your present kernel sources config, copying it into your home directory, then it will clean things up, copy the config from the kernel you're using now into the sources dir, and configure your new kernel. This way you have a config that *works* to start with. The script may ask you some questions about new kernel options. When in doubt, play it safe and choose the default option. Or better, read the kernel documentation! :-)

Now you should be ready to compile the kernel in the way that suits you better: the make "combo" or the make-kpkg way.

If you want you can play with the kernel config with:
```

make menuconfig
```

*before* compiling.

I hope this helps.
Have fun!
Ciao.
-- 
Mac

---

### Post by xenblend on 2006-08-09
While I appreciate your response, I DID configure the kernel, many many times, as I assumed would have been obvious in my post when I said I worked on it for a very long time.

I already knew about oldconfig, but I wanted to try making a kernel from scratch.  As I have now come to understand, devfs is deprecated in 2.6 and is somewhat related to sysfs (two non-related points, just that I learned both of these things today...).

Thank you for your response.

XB

---

### Post by xenblend on 2006-08-09
Well, ok so I guess I didnt mention how long I'd worked on it, but if I didnt know to configure the kernel, I'd be like a baby learning to rock-climb before learning to crawl... :rolleyes: 

XB

---

### Post by MacMan on 2006-08-10
> **xenblend said:**
> While I appreciate your response, I DID configure the kernel, many many times, as I assumed would have been obvious in my post when I said I worked on it for a very long time.

I've learned not to take **anything** for granted when reading a computer-related forum. ;-)

> I already knew about oldconfig, but I wanted to try making a kernel from scratch.

I still think starting from a working kernel gives you the best chances. Trust me, I learned this the hard way. :-)
make oldconfig && make menuconfig , then make small changes every time: if something goes wrong, you'll know the reason.
There are so many options that interact with each other in complicated ways. Why reinvent the wheel?

About your problem, you'll need to be much more precise in reporting the error message you're getting. Otherwise troubleshooting would be far too complicated.

Knowing what you're trying to achieve in this process may be helpful too, I think. Do you need to enable special options or drivers? Or are you just trying to enhance your PC's performances? Have you applied any patches?

Ciao.
-- 
Mac

---

### Post by chesterx on 2008-04-19
Omg.. buds sorry to tell u guys this but
devfs is something back from the 2.4 kernel series, and they put it in 2.6 up to 2.13 for.... legacy compatibility of course.. but the guys behind UDEV (the new /dev etries provider) have told everybody to stop using devfs since the very first 2.16 kernel and people kept using for 7!!! releases of the kernel hhaha
anyway, here is the link , check for it .. the guy's pretty mad :)

[http://www.us.kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs](http://www.us.kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs)

its the real thing from kernel.org

---


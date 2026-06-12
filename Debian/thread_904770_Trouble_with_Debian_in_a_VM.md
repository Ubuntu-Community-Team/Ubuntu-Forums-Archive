---
title: "Trouble with Debian in a VM"
date: 2008-08-29
forum: Debian
---

### Post by Ozor Mox on 2008-08-29
I'm trying to install Debian in a VM and running in to a pretty big problem for something so simple! Here's what I've done:

Downloaded debian-40r4a-i386-netinst.iso*****.
Installed the base system in a VM.
Modified /etc/apt/sources.list to refer to 'testing' instead of 'etch' to update the distribution to newer packages.
Run apt-get update followed by apt-get dist-upgrade to update the package list and upgrade all the installed packages.
Rebooted.

I then get the GRUB screen with two kernels. If I boot into the older one that installed with the base system, everything works great. If I boot into the newer one. I get a load of craziness followed by about 50 lines of

```
<1>BUG: unable to handle kernel <1>BUG: unable to handle kernel
```

all the way down the screen and it does not boot. What am I doing so very wrong?

***** I am aware that I can download an ISO for Debian Testing to install that directly, but I was preferring to stick with the official release and then modify it to how I want it, which I had read was easy using sources.list or Synaptic.

---

### Post by Ozor Mox on 2008-08-29
OK my curiosity got the better of me and I installed Debian in a VM using the Testing image:

debian-LennyBeta2-i386-netinst.iso

It installed the same kernel version but this time it booted up perfectly, so I know it isn't a conflict with my hardware. So although that is essentially my problem solved, why does the method above not work? I have read in various places that this is how to do it and I'd really like to know what I did wrong.

---

### Post by kellemes on 2008-08-30
> **Ozor Mox said:**
> OK my curiosity got the better of me and I installed Debian in a VM using the Testing image:

debian-LennyBeta2-i386-netinst.iso

It installed the same kernel version but this time it booted up perfectly, so I know it isn't a conflict with my hardware. So although that is essentially my problem solved, why does the method above not work? I have read in various places that this is how to do it and I'd really like to know what I did wrong.

Personally I tend to get the iso as close as possible to where I want my system to be. I work with Testing with a little Unstable, and so I always work from a Testing net-install, and modify my sources.list to be able to get the packages from Unstable I need. I use [pinning]("http://jaqque.sbih.org/kplug/apt-pinning.html") for maintaining my mix.

As to why the first method didn't work.. I don't know.
Google only adds to the confusion by providing a hitlist of many thousands, it seems to be some bug in this kernel, but I really don't know. Don't forget that bugs can not only bug you, sometimes they leave you alone. ;-)

---

### Post by Ozor Mox on 2008-08-30
> **kellemes said:**
> Personally I tend to get the iso as close as possible to where I want my system to be. I work with Testing with a little Unstable, and so I always work from a Testing net-install, and modify my sources.list to be able to get the packages from Unstable I need. I use [pinning]("http://jaqque.sbih.org/kplug/apt-pinning.html") for maintaining my mix.

As to why the first method didn't work.. I don't know.
Google only adds to the confusion by providing a hitlist of many thousands, it seems to be some bug in this kernel, but I really don't know. Don't forget that bugs can not only bug you, sometimes they leave you alone. ;-)

Yeah, using the Testing ISO seems to work fine, though I haven't tried modifying that to Unstable yet so I don't know if that will break it again. It is definitely a kernel problem, everything else seems to update perfectly and I can boot fine into the old kernel. It just bugs me when something doesn't work, and I end up spending hours messing with it even if the end result is just "oh that's nice, it works"...I'm sure many here are the same :)

---


---
title: "[SOLVED] 2.6.28-4 with Intrepid"
date: 2009-01-05
forum: General Help
---

### Post by Sypher|NL on 2009-01-05
Hi,

First off; Sorry if this thread is in the wrong category. I thought it would fit here.

I recently bought a notebook; the MSI GX700 (MS-1719). Of course I removed Windows from it and installed Ubuntu for AMD64.

It was all working fine, almost everything (except the webcam, but this can be solved by compiling the drivers) worked out of the box.

But there are some problems with the 2.6.27 kernel, and I am affected by one of those bugs.

The problem is that the Gnome Power Manager sometimes can't see the battery. It gives a big red error and alters my screen's backlight for battery saving. Quite annoying, because the battery is there.

After some research, it was being caused by a bug in the kernel, but this had been fixed by some Intel guy who submitted a patch. For those interested: the information about bug is [here](http://bugzilla.kernel.org/show_bug.cgi?id=9823). That also includes patches. Apparently [this](http://bugzilla.kernel.org/show_bug.cgi?id=12004) bug is related. Either way: a fix was made (again) as the previous one vanished from 2.6.27.

Either way, to fix this bug I wanted to upgrade to 2.6.28-4.

I've downloaded all the related packages and installed the kernel. Headers, Source, restricted modules & image. But dkms fails to build me a fresh nVidia driver ([177.80](http://packages.ubuntu.com/intrepid/nvidia-glx-177)). To work around this problem (according to build.log it cannot determine my kernel version) I tried upgrading to [180.11](http://packages.ubuntu.com/jaunty/nvidia-glx-180). 

This didn't work and gave me an error about the libGl or something. Couldn't make sense of it.

Without the nvidia drivers, my laptop runs (when I booted it into the 2.6.28-4 kernel) at low resolution mode. 

Long thread, so in short:
How can I get Intrepid (2.6.27-9) to run a newer kernel (2.6.28-4) including nvidia drivers?

Thanks!

---

### Post by redilyn on 2009-01-05
**[COLOR="Red"]I suspect this is dangerous and could break your system Proceed with caution!!![/COLOR]**

You can upgrade to this kernel by adding the Jaunty repos temporarily.

```

sudo gedit /etc/apt/sources.list

```

Add the following

```

deb http://archive.ubuntu.com/ubuntu/ jaunty main
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted

```

More info here, Look in the comments section:
[http://www.ubuntugeek.com/new-release-linux-kernel-2628.html](http://www.ubuntugeek.com/new-release-linux-kernel-2628.html)

---

### Post by Sypher|NL on 2009-01-05
> **redilyn said:**
> **[COLOR="Red"]I suspect this is dangerous and could break your system Proceed with caution!!![/COLOR]**


Thanks for your reply. The only thing thats being changed is the Kernel. I've read that it could be done without problems, someone did the same thing but apparently didn't have an nvidia card. I accept the risk, because I'm getting pretty annoyed by the battery bug :)

The update to 2.6.28-4 isn't the real problem here, its the nvidia kernel module that dkms is unable to create.

edit: Seems like I've read the page you gave me and came to the conclusion that it works :)

---

### Post by redilyn on 2009-01-05
I'm not sure but wouldn't the module be updated when you update the kernel using the januty repos?

The thing I would be worried about is version mismatches down the road.

You know, come to think of it. They need testers for jaunty, why not upgrade :)

---

### Post by cariboo on 2009-01-05
Unless you know what you are doing, I would not advise updating  to Jaunty, as it is really broken right now. There is a new version of xorg-xserver that the restricted drivers for Nvidia and ATI won't work with yet. I'm still running the xorg-xserver from Intrepid, I have 37 updates sitting there that I won't upgrade until the restricted drivers are ready.

Jim

---

### Post by Sypher|NL on 2009-01-06
Its a laptop I use on a daily base, so I wouldn't fully upgrade to Jaunty. The only thing I want is the kernel :)

---

### Post by chriswyatt on 2009-01-27
Will the kernel be released for Intrepid through the Intrepid software channels eventually?

---


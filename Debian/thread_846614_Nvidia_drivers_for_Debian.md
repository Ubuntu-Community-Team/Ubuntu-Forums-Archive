---
title: "Nvidia drivers for Debian"
date: 2008-07-01
forum: Debian
---

### Post by Inxsible on 2008-07-01
I have a 32 MB shared nVidia GeForce2 Go card on my old laptop.

According to this [nVidia site]("http://www.nvidia.com/object/IO_32667.html"), it says that I will have to use the legacy drivers 1.0-96xx, and therefore I downloaded those drivers from this [site]("http://www.nvidia.com/object/unix.html"). (linux 32 bit)

But I get errors when I run the command```
sh NVIDIA-Linux-x86-96.43.05-pkg1.run
```
I have to run this in tty, so I can't show you screenshots. But I will list the error messages here```
No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site (ftp://download.nvidia.com)?
```I selected YES. Then I got ```
No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel
``` I selected the only option of OK. Then I got this```
The CC version check failed:

The compiler used to compile the kernel (gcc 4.1) does not exactly match the current compiler (gcc 4.3). The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel.

If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation. Otherwise, select "Yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation. Abort now?
``` I chose Yes and aborted.


Should I choose No and continue and if not, how do I install nvidia drivers for my card?

---

### Post by markharding557 on 2008-07-05
try> CC=/usr/bin/gcc-4.1 sh NVIDIA-Linux-x86-96.43.05-pkg1.run

---

### Post by Inxsible on 2008-07-07
Thanks for the reply...but I had a thread going on in Debian forums and I already tried that and it did not work.

It seems that the linux-header for the kernel I am using are not available in the Lenny repos anymore...and the newer kernels don't recognize my sound card...

So I guess I am stuck between a rock and a hard place.

I guess I will just not use the nVidia drivers on this dino here.


Here's the link to the thread at Debian forums, if you are interested.

[http://forums.debian.net/viewtopic.php?t=28336&highlight=](http://forums.debian.net/viewtopic.php?t=28336&highlight=)

---

### Post by odiseo77 on 2008-07-07
Well, for what I could see in your last post on debian forums, you need the linux-kbuild-2.6.22 package (which match your current kernel). Taken from your post there:

```
#m-a prepare
Getting source for kernel version: 2.6.22-3-686
apt-get install linux-headers-2.6.22-3-686
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
linux-headers-2.6.22-3-686 Depends: linux-kbuild-2.6.22 but it is not installable
E: Broken packages
Creating symlink...
apt-get install build-essential
Reading package list... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

But, for some reason I'm not sure about, this package has been removed from *Testing* repositories and it's not on *Stable* repos either, but [it's on Unstable repository]("http://packages.debian.org/sid/linux-kbuild-2.6.22"), only available for the amd64 architecture, so I'm a bit confused here. (My guess is the package was moved from *Testing* to *Unstable* for security reasons, but I'm not sure at all).

Anyway, the package is simply not available on Lenny's repos (I have it installed here, but it's shown as a local package), and the current Lenny kernel is 2.6.24. So, I guess you haven't upgraded Lenny in a long while? If you don't want to upgrade your whole system (which I would suggest), you will have to upgrade some kernel packages at least:

```
apt-get update
apt-get install linux-headers-2.6.24-1-686 linux-image-2.6.24-1-686 linux-kbuild-2.6.24
```

(or use aptitude, if you prefer).

Then reboot and you should be able to boot the new kernel (2.6.24). After that, you can proceed with the installation of the nvidia driver from a virtual terminal (after having shut gdm or kdm down), executing the export command before. So, if I'm not missing some step, it would be something like (as root):

```
export CC=gcc-4.1
sh NVIDIA-*.run
```

Greetings.

---

### Post by odiseo77 on 2008-07-07
> **Inxsible said:**
> It seems that the linux-header for the kernel I am using are not available in the Lenny repos anymore...and the newer kernels don't recognize my sound card...

oops, sorry, I paid more attention to the thread on debian forums than your last post :oops: so my previous post doesn't make much sense if the new kernel doesn't recognize your sound card. But I think it's really strange newer kernels don't recognize your sound card while the older one does. Have you tried the 2.6.24 kernel? Otherwise, I'm like lost here too :( 

What I would do would be to install the 2.6.24 kernel as I describe above, then try to workaround the sound issue (there must be some fix on the net, mostly considering the old kernel you're using does recognize your sound card), and then install the nvidia driver. If for some reason you don't find some way to get your sound card working with the new kernel, you can always boot the old one.

Sorry if I can't be more helpful here. I remember I had a sound troubleshooting guide for debian on my bookmarks, but I can't find it now. If I find it, I'll post it here.

---

### Post by Inxsible on 2008-07-07
I think you only read the first page of the posts on the debian forums. I mentioned there (on the 2nd page) as well, that my sound drivers didnt work with 2.6.24.

And yes, I have tried those. I actually installed the latest Lenny which gave me 2.6.24...but it just wouldnt load my sound drivers...and I tried a lot of different ways. modprobes and manually installing drivers and also trying to see my /proc/asound - which would always show me "none" even immediately after modprobing.

I had to downgrade the kernel to get my sound to work.

---

### Post by tturrisi on 2008-07-09
re the sound:

Have you tried removing alsa and then manually building and installing the latest alsa from source?  Lenny does not have the latest alsa package but the latest may work w/ your sound card.

You don't say what sound card you have either, what is it?

---


---
title: "'linux-image-386' package installation broke my X server"
date: 2007-07-08
forum: Desktop Environments
---

### Post by PryGuy on 2007-07-08
Hey everybody!

I installed the 'linux-image-386' package yesterday and my X server failed to start. It happend because the 'linux-image-386' package confilicts with (or replaces) 'linux-restricted-modules-2.6.20-15-386' package on installation. I use nvidia restricted driver so it failed to start on the next reboot. I solved the problem reinstalling the 'linux-restricted-modules-2.6.20-15-386' package.

My question is: is that okay or is it an error and I should inform developers about it? Thank you!

---

### Post by kidders on 2007-07-09
Hi there,

I don't think so. Any time you replace your kernel, you will need to reinstall any third-party kernel modules you might have. For many users, this might involve recompiling the source code for a few things they installed manually (eg virtual machines, custom graphics drivers, and so on). For others, it's simply a matter of re-installing a few .deb packages.

Essentially, what you did is a bit like this...

**(Xorg) **-> uses ->** (Graphics drivers) **-> uses ->[B] (Kernel interface)
[/B]
If you suddenly whip the kernel out from under your graphics drivers, and replace it with something new, the whole lot falls apart.

Ordinarily (eg when performing system upgrades), Ubuntu can manage these dependencies for you, but it usually only tries to resolve chains in one direction ... ie "up" the dependency tree (towards the kernel, in my ugly diagram). If you fiddle about, Linux normally expects you to know what you're doing.

I hope that helps.

---

### Post by PryGuy on 2007-07-10
Well, I started from 'nvidia-glx' reinstallation. It didn't help. Do you mean that I had to install a newer version of 'nvidia-glx' or something?

---

### Post by kidders on 2007-07-10
No, not necessarily. Sorry about my last post ... I don't suppose I phrased it very well. :-(

What I was trying to describe is the idea that extras like graphics drivers tend to install themselves into your kernel tree. If you replace (or maybe just reinstall) your kernel, you essentially overwrite any changes made by other packages. So, to put everything back the way it was, you would need to reinstall any such packages. In package management jargon, your kernel is a dependency of your Nvidia drivers, but they are a *reverse* dependency of your kernel. Most Linuxes can handle software dependencies quite nicely, but reverse dependencies are much more complicated to keep track of, which is why Ubuntu let you break X so easily.

Anyhow, you should be able to get X to start again either by ...
[LIST]
[*]Replacing the restricted driver with something more generic, perhaps just on a temporary basis; or
[*]Reinstalling your graphics drivers, so that they can re-do anything that was undone by your kernel reinstallation.
[/LIST]

Sorry for confusing you ... I hope that's a bit clearer!

---

### Post by az on 2007-07-10
> **PryGuy said:**
> 

My question is: is that okay or is it an error and I should inform developers about it? Thank you!

1.  You installed the linux-image package.  Next time, install the linux-* package.  For example:

Instead of running

sudo apt-get install linux-image-386

you should do

sudo apt-get install linux-386

The latter depends on the image and the corresponding restricted modules.


2.  The linux-386 kernel is the generic kernel.  The 386 package exisit to allow people who are running older versions to upgrade to the current version.  You do not need the linux-386 kernel.

---

### Post by PryGuy on 2007-07-11
Thanks for the datailed explainations people! :)

---


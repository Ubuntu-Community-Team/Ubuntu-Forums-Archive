---
title: "wacom-tools-- Built kernel modules? What?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Dawnshadow on 2006-08-08
Hello.

I'm trying to install a utilities package for my Wacom tablet. I found a couple of useful-sounding packages on Synaptic, but I'm unsure how to do what they're asking and Google is unhelpful. The two packages are wacom-tools and wacom-kernel-source. Wacom-tools says...

"This package provides utilities to test and configure wacom graphics tablets.
You will need kernel modules built from the wacom-kernel-source package to
use them with such devices.  It also provides hotplug and udev scripts which
may be useful without these tools and (later) with the wacom support in the
mainline kernel packages as well (2.6.11 or later)."

Unfortunately, I haven't a clue how to build these kernels, although I'm assuming that the terminal and "sudo" will come into play. One of the packages made me install the developer's package when I installed it, so I think I have the tools. I just don't know the command. Could someone please tell me the magic words?

---

### Post by computergroove on 2006-08-08
goto [https://launchpad.net/distros/ubuntu/dapper/+package/wacom-kernel-source](https://launchpad.net/distros/ubuntu/dapper/+package/wacom-kernel-source)
and either compile from the source or I guess download the file and install.

---


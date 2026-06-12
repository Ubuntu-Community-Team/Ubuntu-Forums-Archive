---
title: "USB Keyboard Problem with 6.06 LTS"
date: 2006-07-13
forum: Desktop Environments
---

### Post by rlandrum on 2006-07-13
I'd been running breezy for awhile with this system.  Decided to upgrade to Dapper after having good luck running it at home.

During the install lvm2 failed to install.  Once install aborted, I did gksudo "update-manager -d" again, deselected lvm2 and finished the install without a problem.  I never did get lvm2 installed.

When I boot, the kernel loads and then there's no more USB keyboard response.  Then the graphical login comes up, and I still have no keyboard response.  USB mouse works great though...

Unfortunatly, this is a Dell Optiplex GX280, which has no PS2 connections.  I'm using an ancient, Macally iKey keyboard, which, despite it's age, has worked fine on Redhat, Fedora, Gentoo, Hoary, and Breezy.  I have not yet tried another usb keyboard, as I do not have one.

I've tried what I believe are all the usual tricks.  I disabled hyperthreading, disabled and re-enabled USB support in the BIOS, and tried the acpi=off, pci=noacpi and noapic kernel args, all with no effect.

Any other suggestions (besides installing Breezy)?

Oh...  and just to be clear, this was an upgrade from 5.10 to 6.06 done completely without a CD, in case that matters.

---

### Post by rlandrum on 2006-07-14
One thing I forgot to mention in all this is that this system was originally installed as a 5.04 system...  Hoary.  About 6 months ago I went to Breezy.

---

### Post by rlandrum on 2006-07-14
Well...  Since I got no responses I decided I'd try loading from a 6.06 ISO.  Seems to work like a champ now.

I haven't done a system update since the install, but I suspect that there's something in that list of packages that'll end up being the problem.

Rob

---


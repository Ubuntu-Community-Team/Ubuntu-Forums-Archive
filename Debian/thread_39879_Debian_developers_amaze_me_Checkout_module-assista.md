---
title: "Debian developers amaze me: Checkout module-assistant!"
date: 2005-06-06
forum: Debian
---

### Post by jobezone on 2005-06-06
It's in Universe, and called module-assistant.

After it is installed, run

sudo module-assistant update (updates the kernel modules available to install)
sudo module-assistant

This shows a ncurses dialog (as debconf) where you then select the kernel module you want to install, and it does the rest automatically. For example, nvidia graphic card users would choose the nvidia-kernel. The rest is done automagically.

This package must be recent, and is/will be very usefull !

Here is part of the package's README.Debian in /usr/share/doc/module-assistant/:
> 
Updating the cached data
========================

Do this every time after running "apt-get update", "dselect update", etc.
Run:

  module-assistant update

Listing available packages
==========================

For example, we look for available packages of ALSA. Run:

  module-assistant list alsa

To extend the list to module packages precompiled by Debian maintainers,
replace "list" with "search".

To list all packages, just say "module-assistant list" (or
"module-assistant search"). If you wish to limit the list to the
packages of which you have the source installed, use "li" instead of
"list".

Preparing to compile the own packages
=====================================

Run:

  module-assistant prepare

Building and installing packages for the own kernel
===================================================

Assuming that there is no precompiled ALSA package available for your
kernel.  Run:

  module-assistant auto-install alsa

And be patient...

For more commands and options, see the manpage of module-assistant.


---

### Post by jobezone on 2005-06-06
ahh, I saw lm-sensor-source, tried to install, but it said there was no installable package. It seems it isn't in Ubuntu's repositories, but is in Debian's (stable, testing and unstable). I'm going to have to temporarily add debian sarge's repository for this to work. This is a setback if ubuntu doesn't contain these lovely module kernel packages.

---

### Post by jobezone on 2005-06-06
[QUOTE=jobezone]ahh, I saw lm-sensor-source, tried to install, but it said there was no installable package. It seems it isn't in Ubuntu's repositories, but is in Debian's (stable, testing and unstable). I'm going to have to temporarily add debian sarge's repository for this to work. This is a setback if ubuntu doesn't contain these lovely module kernel packages.[/QUOTE]
 ah, it failed when I tried to install lm-sensor-source, and the log it pointed me to said l-sensors was already in the linux 2.6 package.

---


---
title: "System freezes on shutdown"
date: 2015-01-10
forum: Desktop Environments
---

### Post by kuckunniwi on 2015-01-10
Hi,

I was wondering if anyone might be able to provide a bit of insight into a problem I'm having with a brand new Acer ES1-311-P4P0 (Processor: Intel N3540).

Bought it recently for my mother, did a clean install of Xubuntu 14.04 amd64, and overall, the system is working fine. Function keys mostly work, except for screen brightness and wireless on/off.

The issue I'm having is that the system freezes one out of 4 times, when shutting down --it gets stuck on the Xubuntu logo and doesn't power off. This is the case regardless of whether I shut down from the menu or from a terminal (*sudo poweroff now*). System freezes also happen every now and then when in the middle of working, browsing, etc.

I've googled the *symptoms* and all the answers I've found were all related to ATI video cards, something that this laptop doesn't have (integrated intel hd).

What could be the source of this problem? Kernel-related? Xubuntu-related?

If I run a live session with a different distro, would the lack of freezes on the live session mean anything in terms of them not occurring once the distro has been installed?

Thanks a bunch, particularly with your patience! :)

---

### Post by ibjsb4 on 2015-01-11
I don't know if it is kernel related, but you could try the newer 3.16 kernel.

---

### Post by Kirkx on 2015-01-12
I had shutdown problems with my Xubuntu 14.04 on a desktop. The solution was to stop using the "shutdown" button and either shutdown from the terminal:

sudo shutdown -h now

or use the "restart" button and then shutdown from the boot menu. I'm not sure if Grub2 boot menu has shutdown option because I use another bootloader (Grub4Dos),

---

### Post by flaymond on 2015-01-12
I just use 'sudo poweroff' to shut down and 'sudo reboot'.

---

### Post by kuckunniwi on 2015-01-13
Thanks Kirkx. *sudo shutdown -h now* seems to be doing the trick. Why would that work, when *sudo poweroff now* does not? (at least not in my case)

---

### Post by kuckunniwi on 2015-01-14
Actually, no, *sudo shutdown -h now* isn't doing the trick after all. It looks like it's dependant on how long the computer has been on.

I read something elsewhere about acpi service possibly having something to do with it.

---


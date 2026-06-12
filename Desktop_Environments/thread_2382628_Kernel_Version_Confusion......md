---
title: "Kernel Version Confusion.....?"
date: 2018-01-15
forum: Desktop Environments
---

### Post by mongo42 on 2018-01-15
Hi all,

I am currently running Ubuntu 16.04 LTS (I'm the other person on the planet who likes Unity), and just upgraded the kernel over the weekend.  The upgrade was from v4.10 to 4.13.  As suspected, this broke my VMWare Workstation 12.5.7 installation (it is only good up to kernel v4.12), and I ended up regressing the kernel back to 4.10 (my VMs are critical) via grub2.  My only concern with this is whether the other updates that came at the same time were dependent on v4.13, and if the regression broke them.  In any case, I was reading up on the new kernel releases over the week in response to Meltdown/Spectre, and the kernel versions mentioned are 4.4.0.108 and 4.4.0.109.  So, why am I at v4.10 (or even 4.13)...?!?  Am I confusing the version numbers?  Thanks!

Mongo

---

### Post by DuckHook on 2018-01-15
Versions of Xenial from 16.04.3 onward included the _H_ard_w_are _E_nablement stack which mirrors the kernel series being used in the latest version. Versions of Xenial before 16.04.3 stayed with the original kernel series (4.4). You seem to have installed 16.04.3 and are getting the series that is currently in Artful (17.10). The reason for the jump from 4.10 to 4.13 was due to the Meltdown/Spectre fiasco… the developers just decided to move the next series up by a few months rather than patch a series that would be left behind in weeks.

If the newest kernel breaks VMWare and it is a mission-critical app for you, then of course you should keep your box operating first. However, the security hole being closed is a real one, so you should keep an eye open for further updates down the road which may close those security holes without borking VMWare. Also, you can try upgrading to a newer VMWare to see if that helps. This same problem occurred in VirtualBox and most problems were solved by users upgrading from 5.0 to 5.2.

---

### Post by mongo42 on 2018-02-13
Thanks, DuckHook!  I am now looking at regressing back to kernel 4.4, and staying pat there for the time being.  My understanding is that it has all of the functionality I need, and I can still receive security updates (sans the Meltdown/Spectre stuff).  My only concern is that updates for other applications might be HWE-specific, in which case upgrading would break them, but I will deal with that on a case-by-case basis.  All the while, I will be watching the boards (and the kernel release change logs) for a fix.  I am considering upgrading to Workstation ver 14, but at the current time ver 12 works perfectly (other than the kernel thing, of course)...

---

### Post by vasa1 on 2018-02-14
> **mongo42 said:**
> ... My only concern is that updates for other applications might be HWE-specific, in which case upgrading would break them, ...
Nobody can say that that isn't a possibility but are there any reports of that actually happening? I haven't come across such reports although kernel updates breaking VMs goes back years if net searches are anything to go by.

FWIW, [VirtualBox Guest Additions to be Included in Linux Kernel]("http://www.omgubuntu.co.uk/2018/01/virtualbox-guest-additions-linux-kernel") in 4.1_6_ or later.

---

### Post by kc1di on 2018-02-14
Unless you need the funtionality of 4.10 I'd regress back to 4.4 which will be supported until 2021.  4.10 is already end of life. and will not get updates for security.
4.4 and 4.13 have been updated for spectre and meltdown but 4.13 reaches end of life this soon. you can follow it[ here.]("https://wiki.ubuntu.com/Kernel/Support")

---


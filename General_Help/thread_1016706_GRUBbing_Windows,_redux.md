---
title: "GRUBbing Windows, redux"
date: 2008-12-20
forum: General Help
---

### Post by mhenriday on 2008-12-20
Once again I find it necessary to re-install the two **Windows** OS (**XP** and **Vista**) on my triple-boot machine, and would like to find a way to do so which leaves me with access to **GRUB**, so that I can avoid re-installing **Intrepid** as well. I started a [**_[COLOR="Blue"]thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=494700") with a similar inquiry more than a year ago, but as the last activity there took place before the 20080421 archive cutoff, I am unable now to post to that thread.  **Geek_man** was kind enough to reply there with the following suggestion :
> Everytime you reinstall Vista, you should pop in the Ubuntu Live CD and in the termina run :
```
grub-install /dev/sdb
```
Please verify this first, it's been a long while since I've dealt with this stuff. If you boot from your first HD, then change /dev/sdb to /dev/sda. Like I said, verfiy this...
but unfortunately, when on the occasion of a subsequent **Windows**-OS re-installation I attempted to follow his advice, it failed to work, and in the end I was forced to re-install **Ubuntu** in order to regain access to **GRUB**. Any other suggestions as to how one can retain **GRUB** when re-installing **Windows** OS on a multiple-boot machine ?...

Henri

---

### Post by taurus on 2008-12-20
Maybe this link helps.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by mhenriday on 2008-12-21
**Taurus**, many thanks for the link ! The Desktop/Live CD method seems the simplest and most foolproof, so I'm thinking of trying that as soon as I get my courage up. As I upgraded to (64-bit) **Intrepid** directly from **Hardy**, I didn't bother to burn a new CD for the former ; may I therefore ask you if am I right in supposing that I can use my **Hardy** disc to re-install **GRUB** on my MBR, or should I burn an **Intrepid** CD first ?...

Henri

---

### Post by mhenriday on 2009-02-11
**Tauris**, just a line to thank you once again for the link above to the documentation on how to re-insert **GRUB** into the **MBR** ! It proved invaluable after I ran into problems with my **XP** installation and had to re-install. By the way, I encountered no difficulties using the Live CD for **Hardy** to run the «Quick Start» option, which worked like a charm....

Henri

---


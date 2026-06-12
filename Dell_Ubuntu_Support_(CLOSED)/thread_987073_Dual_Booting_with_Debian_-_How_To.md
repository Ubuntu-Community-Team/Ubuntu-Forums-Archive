---
title: "Dual Booting with Debian - How To?"
date: 2008-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iaskedalice09 on 2008-11-19
I know it is possible to dual boot Linuxes (Linuxi?), I'm just not sure how to do it. Any advice? Has anyone here done it? 

I know there's Lubi but that's for people that have another distro and want to add on Ubuntu. If there is a Lubi but boots Debian instead of Ubuntu I would LOVE love LOVE that!

Please tell me if this is not an appropriate forum and a Debian forum would be more suitable. I love Ubuntu but wanna play around with Debian a bit.

Todah,
bobby

---

### Post by notwen on 2008-11-19
If you'remore comfortable installing Debian onto a virtual machine, perhaps you would want to look into [VirtualBox]("http://www.virtualbox.org/wiki/Linux_Downloads") or [VMWare]("http://www.vmware.com/download/server/").  If you;re just wanting to explore/learn a distro this is always a good option, as you don't mess w/ your current installation plus you can move from your actual machine and your virtual machine should you need access to both simultaneously.  Which is generally the case when exploring/tinkering w/ a new distro.  =]

how-tos for each:
[VirtualBox]("http://ubuntuforums.org/showthread.php?t=828927")
[VMWare]("http://ubuntuforums.org/showthread.php?t=779934")

---

### Post by snowpine on 2008-11-19
Hi there,
The simple answer to your question is that you can create a new partition on your hard drive and install Debian onto the new partition. The last step in the install process is installing the Grub boot loader, which is smart enough to detect your existing Ubuntu install and give you both options when you boot the computer.

Other ways to experiment with Debian and see if you like are: 1) install it in a virtual machine (Virtualbox or the like), or 2) try the Live CD provided by the Debian Live project ([http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)).

I am not familiar with Lubi, so I can't give you any advice there.

Good luck!

---

### Post by bapoumba on 2008-11-19
TO the OP: are you using Dell hardware ? (You posted in the Dell forum).

---


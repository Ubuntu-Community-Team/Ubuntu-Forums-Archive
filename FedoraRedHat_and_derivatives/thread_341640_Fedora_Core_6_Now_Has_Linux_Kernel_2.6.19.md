---
title: "Fedora Core 6 Now Has Linux Kernel 2.6.19"
date: 2007-01-18
forum: Fedora/RedHat and derivatives
---

### Post by deweese on 2007-01-18
Wow this Fedora is really advancing fast.  I switched to it from Edgy Eft. I love it.
The Linux kernels are more updated than Ubuntu.  See for yourself.
2.6.19 is here today!  I am just bragging.

---

### Post by siucdude on 2007-01-18
That is fine. Ubuntu Feisty has 2.6.20-5.  Good luck with fedora

---

### Post by deweese on 2007-01-19
Thank you very much.  Btw, I was referring to STABLE. :-)

The latest stable version of the Linux kernel is:  	2.6.19.2 	2007-01-10 19:11 UTC 	F 	V 	VI 	C 	Changelog

see [www.kernel.org](www.kernel.org)

---

### Post by xabbott on 2007-01-21
What does this matter? Whatever is released last will have the latest kernel. OR *gasp* you can compile the latest kernel yourself for any distro. Or use something like Arch :biggrin: and always have the lastest kernel...

---

### Post by po0f on 2007-01-21
xabbott,

I think the point deweese was trying to make is that FC continue to update/upgrade the kernel throughout a release, as opposed to Ubuntu's stance of just releasing the same kernel version with security patches applied as an update.

---

### Post by xabbott on 2007-01-21
> **po0f said:**
> xabbott,

I think the point deweese was trying to make is that FC continue to update/upgrade the kernel throughout a release, as opposed to Ubuntu's stance of just releasing the same kernel version with security patches applied as an update.

Ah, true. ](*,) 

Although, I wouldn't call this Ubuntu's stance. Slackware, Suse, Debian, and generally those based on them do this. The only distros I know that constantly update all packages are Gentoo, Archlinux, and rPath. I'm sure there are others but I can't remember or don't know of them. Is this common for Red Hate/Fedora? Or was this due to a severe bug/exploit?

---

### Post by po0f on 2007-01-21
xabbott,

It has been common since FC5 (I've only used 5 and 6), and I'm sure it will continue.  I'm sure at some point Dapper will get a kernel upgrade.  One, 2.6.15 is ancient; and two, it is an LTS release (could you imagine using 2.6.15 2 years from now?  :D).

Since Dapper is the first LTS release, I'm guessing that Ubuntu hasn't decided on a kernel upgrade strategy yet.  I'll try to dig up some info on it.

---

### Post by givré on 2007-01-24
> **po0f said:**
> xabbott,

It has been common since FC5 (I've only used 5 and 6), and I'm sure it will continue.  I'm sure at some point Dapper will get a kernel upgrade.  One, 2.6.15 is ancient; and two, it is an LTS release (could you imagine using 2.6.15 2 years from now?  :D).

RHEL4 still use 2.6.9 you know...
Upgrading a kernel could lead to regression, and that's why the ubuntu policy is to not upgrade kernel. 
However, they apply security patch and upgrade drivers when possible.

---

### Post by Insomniac20k on 2007-01-27
What's the advantage of upgrading the kernel constantly? Does it change all that much

---

### Post by Rodneyck on 2007-01-28
> **Insomniac20k said:**
> What's the advantage of upgrading the kernel constantly? Does it change all that much

Better hardware support and detection for one.

---

### Post by xabbott on 2007-01-29
> **Rodneyck said:**
> Better hardware support and detection for one.
The kernel doesn't handle hardware detection.

---

### Post by pissedoffdude on 2007-02-02
Yeah I had a pretty big problem when I updates the kernel.  I wouldn't be able to boot as grub wouldn't load.  It would just say GRUB: and it wouldn't go anywhere.  I was able to use the rescue disk to reinstall grub but still it shouldn't have made that mistake.

---


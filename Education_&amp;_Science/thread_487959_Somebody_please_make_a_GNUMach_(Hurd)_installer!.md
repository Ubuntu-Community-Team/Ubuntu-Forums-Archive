---
title: "Somebody please make a GNU/Mach (Hurd) installer!"
date: 2007-06-29
forum: Education &amp; Science
---

### Post by glotz on 2007-06-29
See e.g. [http://www.debian.org/ports/hurd/hurd-install](http://www.debian.org/ports/hurd/hurd-install)

I think this is topical now because it looks like the Linux kernel might stay on the soon-to-be obsoleted GPL2.

---

### Post by Lord Illidan on 2007-06-29
I thought Torvalds liked the new revisions of GPL 3..

---

### Post by glotz on 2007-06-29
Not really. AFAIK he just disliked it a bit less. Besides this isn't just about Linus.[quote="[news.com](http://news.com.com/8301-10784_3-6171300-7.html) about Linus on GPL3"]Torvalds was noncommittal about whether he might try to move the Linux kernel to GPL 3--a change that would require the permission not just of Torvalds but also of all other Linux kernel copyright holders. But he didn't rule it out.

"The current draft makes me think it's at least a possibility in theory, but whether it's practical and worth it is a totally different thing," he said. "Practically speaking, it would involve a lot of work to make sure everything relevant is GPLv3-compatible even if we decided that the GPL 3 is OK."

DRM remains a sticking point. The Free Software Foundation drafting the document wants to prohibit hardware companies such as TiVo from imposing restrictions on GPL software used in their products, but Torvalds believes that should be permitted.[/quote] And I think this would be very beneficial for the GNU project regardless of the fate of the Linux kernel. And Linus is on the wrong team here, if you ask me.

---

### Post by deanlinkous on 2007-06-29
I am hoping the sun kernel goes v3....

---

### Post by glotz on 2007-07-13
Linus bashes GPLv3, making this thread more important [http://linux.slashdot.org/article.pl?sid=07/07/13/2123235](http://linux.slashdot.org/article.pl?sid=07/07/13/2123235)

---

### Post by jinx099 on 2007-07-13
I think I'd rather have an openSolaris kernel, or maybe a *BSD.  Nexenta looks promising, but needs work!

---

### Post by glotz on 2007-07-14
I think that *BSD is nice but the license is too weak. Nexenta could be interesting, agreed.

---

### Post by WebDrake on 2007-07-15
> **glotz said:**
> Linus bashes GPLv3, making this thread more important [http://linux.slashdot.org/article.pl?sid=07/07/13/2123235](http://linux.slashdot.org/article.pl?sid=07/07/13/2123235)

Except that this article is completely misleading crap constructed by wrenching way out of context some quotes from what was in practice a polite and well-argued case, not for why GPLv3 is bad, but for why Linus Torvalds personally doesn't feel it's the right license for his code:

[http://lkml.org/lkml/2007/6/20/223](http://lkml.org/lkml/2007/6/20/223)

---

### Post by WebDrake on 2007-07-15
> **glotz said:**
> See e.g. [http://www.debian.org/ports/hurd/hurd-install](http://www.debian.org/ports/hurd/hurd-install)

I think this is topical now because it looks like the Linux kernel might stay on the soon-to-be obsoleted GPL2.

GPLv3 has only been out a few weeks and it will take many projects (not just Linux) time to decide whether it's the right license or not for them.

In any case, Linux won't magically become non-free software because it stays with GPLv2.  The fact that in principle GPLv2 has some issues doesn't mean that in practice this has to be a problem for any given piece of software, the kernel included.  I would give it *at least* a couple of years before passing any judgement on kernel licensing.

I think it would be a great thing to expand the choice of kernels available to users of Debian, Ubuntu and other distros but this sort of, "Oh my God, Linux may stay with v2, we must jump ship now!!" attitude just seems silly, especially when the alternatives have plenty of drawbacks of their own.

I mean, consider the Solaris kernel.  It's technically nice, it may well be released with GPLv3 in the future (and even CDDL doesn't really cause a licensing problem AFAIK) but on the other hand it is still the property of one single large commercial entity.  I would love to see it as an *option* for Ubuntu users---to have Nexenta merged into the official Ubuntu family---but I think it would be crazy to abandon Linux for it.  The idea of key parts of our OS being owned by a single corporate gatekeeper---even if they are GPLv3 licensed---is far more worrying to me than the idea of continuing with GPLv2 on a kernel that is independently developed and where copyright remains in the hands of the contributors.

---

### Post by az on 2007-07-15
> **glotz said:**
> 
I think this is topical now because it looks like the Linux kernel might stay on the soon-to-be obsoleted GPL2.

There is nothing wrong with GPLv2.  In fact, I reckon it will take a few years before most of the free-libre software projects migrate to it.  And that's not because they have patent investments or hardware/DRM issues that make GPLv3 problematic for them, but just because it is new and needs to be tested out.

No big deal.  Even if the linux kernel never used GPLv3, big deal.  Get over it.  So long as enough code is released as v3.  Your whole OS doesn't have to be v3 for it's new protections to take effect.


Anyway, to answer your question:

andy@emma-desktop:~$ apt-cache search crosshurd
crosshurd - Install a Debian system
andy@emma-desktop:~$ apt-cache show crosshurd
Package: crosshurd
Priority: extra
Section: universe/misc
Installed-Size: 172
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Jeff Bailey <jbailey@raspberryginger.com>
Architecture: all
Version: 1.7.26
Depends: dialog, dpkg-dev
Recommends: attr
Filename: pool/universe/c/crosshurd/crosshurd_1.7.26_all.deb
Size: 19952
MD5sum: 7ab1b780850ce63287bc056222060f59
SHA1: 63c833f0151524e8e1f22c7ffb69d418e2ccb9d3
SHA256: be153503cd7f338ead4962e7dca4759c1673121e9f3127338c8831c45e785ae7
Description: Install a Debian system
 crosshurd uses apt and a bit of black magic to setup a functional
 Debian system. It supports the following target systems:
  - linux-gnu (GNU/Linux)
  - gnu (GNU/Hurd)
  - kfreebsd-gnu (GNU/kFreeBSD)
  - knetbsd-gnu (GNU/kNetBSD)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---


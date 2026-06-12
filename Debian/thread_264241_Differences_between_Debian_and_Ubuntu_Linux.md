---
title: "Differences between Debian and Ubuntu Linux"
date: 2006-09-24
forum: Debian
---

### Post by Xilon on 2006-09-24
There are similar threads around on the forum but none really answer my main question; what's the difference between Debian and Ubuntu?

We all know Ubuntu is based on Debian - unstable, but how is it different? I ran Debian Etch on VMWare and I must say it's very similar to ubuntu. The main differences I noticed were that the "Administration" menu is a lot more empty, whether that effects how easy the Distro will be to use I don't know yet. I noticed that firefox was version 1.5.0.4, though the unstable version probably has a 2.0 beta or at least the newest firefox, Etch seems to be a bit behind Ubuntu (not to mention Edgy having 2.0b2).

I like being "bleeding edge", at least for the apps I use like Firefox, which is why I'm running Edgy atm, and loving it btw. How far behind Ubuntu is Debian (testing)? How far behind Ubuntu is Debian (unstable)? If Debian unstable is relatively stable then I don't really see why I should be using Ubuntu.

When running Debian testing can I use repositories from Debian Unstable or possibly even Ubuntu without screwing up the system completely? I'm guessing that compatibility with Ubuntu wouldn't be too great since Ubuntu has many distro-specific metapackages.

How easy is it to use Debian compared to Ubuntu? The basic functionality seems to be pretty much the same. If I'd want to install compiz for instance would it be any harder on Debian than in Ubuntu? Would the repositories for Ubuntu on compiz.net also work on Debian or are there any dependency conflicts? I noticed that Debian Etch uses the same version of xserver-xorg as Ubuntu Edgy so I guess it wouldn't be too hard to set that up.

Basically I'd like ot know if it's worth staying with Ubuntu or should I go to Ubuntu's roots and check out Debian? I like to play with the system, it's the reason I started using Linux, I wanted to go Slackware but I got hooked on the debian packaging system :P. As I mentioned before I would also like to have the most bleeding edge software, which Ubuntu tends to offer, would I get the same kind of treatment with Debian? Oh and one last thing... the all important community and support - how does it compare? I love these forums, the people here and the amount of support given. There are heaps of howto's etc that have made using Ubuntu really easy. I've heard that Debian users are elitist and don't tend to be friendly to n00bs, which also reminds me of Gentoo :P Is this true? Would the ubuntuforums also help a Debian user? :)

Thank you for any input.

---

### Post by qamelian on 2006-09-24
> **Xilon said:**
> There are similar threads around on the forum but none really answer my main question; what's the difference between Debian and Ubuntu?

We all know Ubuntu is based on Debian - unstable, but how is it different? I ran Debian Etch on VMWare and I must say it's very similar to ubuntu. The main differences I noticed were that the "Administration" menu is a lot more empty, whether that effects how easy the Distro will be to use I don't know yet. I noticed that firefox was version 1.5.0.4, though the unstable version probably has a 2.0 beta or at least the newest firefox, Etch seems to be a bit behind Ubuntu (not to mention Edgy having 2.0b2).

I like being "bleeding edge", at least for the apps I use like Firefox, which is why I'm running Edgy atm, and loving it btw. How far behind Ubuntu is Debian (testing)? How far behind Ubuntu is Debian (unstable)? If Debian unstable is relatively stable then I don't really see why I should be using Ubuntu.

When running Debian testing can I use repositories from Debian Unstable or possibly even Ubuntu without screwing up the system completely? I'm guessing that compatibility with Ubuntu wouldn't be too great since Ubuntu has many distro-specific metapackages.

How easy is it to use Debian compared to Ubuntu? The basic functionality seems to be pretty much the same. If I'd want to install compiz for instance would it be any harder on Debian than in Ubuntu? Would the repositories for Ubuntu on compiz.net also work on Debian or are there any dependency conflicts? I noticed that Debian Etch uses the same version of xserver-xorg as Ubuntu Edgy so I guess it wouldn't be too hard to set that up.

Basically I'd like ot know if it's worth staying with Ubuntu or should I go to Ubuntu's roots and check out Debian? I like to play with the system, it's the reason I started using Linux, I wanted to go Slackware but I got hooked on the debian packaging system :P. As I mentioned before I would also like to have the most bleeding edge software, which Ubuntu tends to offer, would I get the same kind of treatment with Debian? Oh and one last thing... the all important community and support - how does it compare? I love these forums, the people here and the amount of support given. There are heaps of howto's etc that have made using Ubuntu really easy. I've heard that Debian users are elitist and don't tend to be friendly to n00bs, which also reminds me of Gentoo :P Is this true? Would the ubuntuforums also help a Debian user? :)

Thank you for any input.
For me, the best reason for choosing Ubuntu over Debian is that Ubuntu essentially works out of the box on both my computers and Debian doesn't. A fresh Debian install leaves X broken on both my systems requiring some fiddling to get it working. Same thing with my sound card on my laptop. On Ubuntu, it just works (barring a few issues in Dapper that seem to be fixed in Edgy). I have yet to get my sound working in Debian.

These are Just two examples, but my experiences comparing the Ubuntu and Debian result in Ubuntu being what you get from Debian with mucking about for a week sorting out problems. It's Debian for regular end-users who don't have time to waste on fixing things and just want to get some work done!

---

### Post by RAV TUX on 2006-09-24
working out-of the box is one reason I use Knoppix over Ubuntu.

---

### Post by Xilon on 2006-09-24
Do you have some obscure hardware or something? It's quite shocking to hear X being broken after installing a stable distro... (Though I did get that while upgrading from Dapper -> Edgy, not that Edgy is stable...). If hardware problems is the only issue then I'm willing to give Debian a try (since hardware varies, as do the issues, from computer to computer). If debian fails to work with my hardware then I might go back to Ubuntu.

---

### Post by qamelian on 2006-09-24
> **yozef said:**
> working out-of the box is one reason I use Knoppix over Ubuntu.

Knoppix works fine on my desktop PC but fails to work properly with the sound card on my laptop. It causes sound to stutter wildly making the laptop almost unusable. I also found Knoppix installed to my hard disc substantially slower than Dapper on my desktop PC. 

It is one of the better live CDs though.

---

### Post by qamelian on 2006-09-24
> **Xilon said:**
> Do you have some obscure hardware or something? It's quite shocking to hear X being broken after installing a stable distro... (Though I did get that while upgrading from Dapper -> Edgy, not that Edgy is stable...). If hardware problems is the only issue then I'm willing to give Debian a try (since hardware varies, as do the issues, from computer to computer). If debian fails to work with my hardware then I might go back to Ubuntu.

Nope, I have an Nvidia Geforece FX 5600 on the desktop PC and an ATI Radeon Mobility 9000 IGP on the laptop. Debian and Slackware are the only distros that give me any grief on these too systems. Even Gentoo was relatively painless (although time-consuming) to get working.

---

### Post by az on 2006-09-24
Debian stable is really stable and slow-moving.  Debian Unstable is really fast-paced, a challenge to use and is pretty much as close to bleeding-edge as you would want to be.

Ubuntu takes a small portion of the Debian unstable packages them and patches them to work well and supports them.  The release cycle is a predictable six-month period.  The reason Ubuntu can release that often is that they only take into account the small subset of packages that are supported.

No, you cannot use Debian repos.  You may compile the packages from source packages, but not the binaries.

But please, go and have fun and run Debian unstable.  Use debianhelp.org for forum help.

[http://www.debianhelp.org/](http://www.debianhelp.org/)

---

### Post by Xilon on 2006-09-25
So it seems like I wouldn't really miss out on anything changing to Debian, apart from Ubuntu possibly being a bit more user-friendly and polished.

I'm downloading the DVD now and I'll give it a try as soon as it's downloaded. I'll probably do as someone suggested in another thread with installing the stable and having a chroot jail for unstable apps since I really only want a few bleeding edge apps.

---


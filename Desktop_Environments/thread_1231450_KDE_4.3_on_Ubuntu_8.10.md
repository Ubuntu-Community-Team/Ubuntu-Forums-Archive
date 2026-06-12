---
title: "KDE 4.3 on Ubuntu 8.10"
date: 2009-08-04
forum: Desktop Environments
---

### Post by ckyidr9 on 2009-08-04
After getting KDE 4.2 install successfully on Ubuntu 8.10 I attempted to install KDE 4.3 RC2 which seemed to only half installed / stoped KDE from starting altogether.

With KDE 4.3.0 released today, does anyone know what repository I could get it from for Intrepid? 

I don't what to go to (k)Ubuntu 9.04 because of a lack of decent drivers for my "legacy" ATI card.

---

### Post by smsmith on 2009-08-04
> **ckyidr9 said:**
> After getting KDE 4.2 install successfully on Ubuntu 8.10 I attempted to install KDE 4.3 RC2 which seemed to only half installed / stoped KDE from starting altogether.

With KDE 4.3.0 released today, does anyone know what repository I could get it from for Intrepid? 

I don't what to go to (k)Ubuntu 9.04 because of a lack of decent drivers for my "legacy" ATI card.
With respect to your "legacy" ATI card:  I too have one of those (it's a Radeon 1200 [RS690]), and I have managed to cure all my ills with it.

What I did, was installed the updated ATI and Radeon drivers from here:
[https://launchpad.net/~tormodvolden/+archive/ppa]("https://launchpad.net/%7Etormodvolden/+archive/ppa")

Specifically, I installed these two packages:
[https://launchpad.net/~tormodvolden/+archive/ppa/+build/1113483/+files/xserver-xorg-video-ati_6.12.99+git20090710.43db263d-0ubuntu0tormod_i386.deb]("https://launchpad.net/%7Etormodvolden/+archive/ppa/+build/1113483/+files/xserver-xorg-video-ati_6.12.99+git20090710.43db263d-0ubuntu0tormod_i386.deb")
[https://launchpad.net/~tormodvolden/+archive/ppa/+build/1113483/+files/xserver-xorg-video-radeon_6.12.99+git20090710.43db263d-0ubuntu0tormod_i386.deb]("https://launchpad.net/%7Etormodvolden/+archive/ppa/+build/1113483/+files/xserver-xorg-video-radeon_6.12.99+git20090710.43db263d-0ubuntu0tormod_i386.deb")

When I first restarted X, my display was stuck at something like 800 x 600.  So I had to edit my xorg.conf to include "Driver" "ati" in the Device section, which I learned here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/379856/comments/2](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/379856/comments/2)

On the next restart of X, the display resolution was correctly identified and applied.

So, even with having this "legacy" driver, I am able to use Jaunty, with any desktop effects enabled (no more flicker, which was the problem I was having).

You then need only enable the backports repository and KDE 4.3 will install during your next update.

If you choose to stay on 8.10, I suppose you could try adding the jaunty-backports repositories listed on this page:
[http://www.kubuntu.org/news/kde-4.3](http://www.kubuntu.org/news/kde-4.3)

I'd be careful doing that.

---


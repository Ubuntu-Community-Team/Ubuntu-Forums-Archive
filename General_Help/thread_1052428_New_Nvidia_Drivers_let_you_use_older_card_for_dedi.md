---
title: "New Nvidia Drivers let you use older card for dedicated physics... kills Xorg?"
date: 2009-01-27
forum: General Help
---

### Post by Ryan Marcus on 2009-01-27
Due to the recent NVidia driver update, (link: [http://www.nvidia.com/object/winvista_x86_181.22_whql.html]("http://www.nvidia.com/object/winvista_x86_181.22_whql.html")) you can use an old GeForce 8 or higher card in combination with another GeForce 8 or higher card for dedicated physics processing...

I had to give it a try... I put my old 8600 into my secondary PCI slot, and booted up into Vista -- it worked. I was pretty happy, because that also met I could have three monitors (four, really.)

Anyway, it wasn't so great when I tried to boot into Ubuntu... Xorg wouldn't start. I tried the basic stuff, including running xfix from recovery mode, but it didn't have any effect.

I've noticed the most recent Linux drivers (on the NVidia site) are 180.22, whereas the Windows drives are at 181.22... Is this Xorg problem fixable?

How long does it take for Linux drivers to roll out?

EDIT:

Ah! I figured it out... here is my blog post detailing the whole thing: [http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/)

---


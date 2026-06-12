---
title: "Nvidia HDTV Output Red Channel is Wonky"
date: 2007-03-26
forum: Desktop Environments
---

### Post by JamonTerrell on 2007-03-26
Hi,

I'm using the binary nvidia drivers, so I realize there may not be a lot that any of you can provide in the way of resolving the problem, but I'm at least curious if anyone else has experienced it.

The problem appears to be limited to my software/settings/drivers under linux.  The same hardware functions properly under Windows.  I'm running Feisty Beta (while I haven't verified, I'd expect it to be unchanged under other distributions).  I'm also running an x86_64 (AMD64) architecture... which could more likely be related to the issue.

Imagine a gradient in red from 0 to 255.  The gradient appears correct from values 0-15.  Once you hit value 16, it's observed to be the same color as somewhere around value 8.  This phenomenon continues repeating itself at every 16 shade segment all the way to pure bright red.  This is only observed in the Red Channel, Green and Blue are both perfectly normal.  In addition, this only occurs on my HDTV, which, as I mentioned before, works perfectly fine in Windows over the same DVI->HDMI cable.  I've attached some shots of the same gradient taken with my Digital camera on both my LCD and my HDTV.  Please forgive the bad shots, it's very difficult to take pictures of display devices.  Though the blue looks slightly wonky in the photograph, it appears fine in person.  The Red effect is actually more obvious in person than the photograph displays.

I've also attached my Xorg log and my Xorg.conf files.  I've tried many things for the Xorg.conf, which is why i have so many strange settings on it now... all settings have the same effect.

Thanks for any help you can provide,
Jamon Terrell

[ATTACH]28293[/ATTACH]

[ATTACH]28294[/ATTACH]

[ATTACH]28295[/ATTACH]

[ATTACH]28296[/ATTACH]

[ATTACH]28297[/ATTACH]

---


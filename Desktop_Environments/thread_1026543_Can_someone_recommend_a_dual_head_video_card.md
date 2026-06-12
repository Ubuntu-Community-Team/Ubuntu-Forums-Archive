---
title: "Can someone recommend a dual head video card?"
date: 2008-12-31
forum: Desktop Environments
---

### Post by webtent on 2008-12-31
I have had no luck with either my Matrox or Nvidia dual head cards. The
Matrox G550 does not support the DVI 1440x900 resolution of my monitor
and my Nvidia FX5500 card is completely unacceptable causing high Xorg
cpu usage with every move on my desktop. I did not receive any
suggestions for getting my Nvidia card to work well after a couple of
previous posts, I've tried so many things from different posts and
suggesttions in my xorg.conf, but still no help. So, I am now asking for
any recommendation from anyone who knows of a card that would work well
in my environment.

All worked great with two LCD 17" monitors and my Matrox card for a long
time. One of those monitors died and I bought a new ASUS widescreen and
still struggling to get it to work well. I want to use the DVI input for
my new monitor with the 1440x900 resolution, can some suggest something
they know works well from experience?

---

### Post by CHaoSlayeR on 2009-01-10
Hi there,

I know your problem. At work I have very good experiences made with AMD/ATI Radeon X1xxx cards and the open source radeon driver. So respecting that you said you tried everything and nothing works (although I think at least with the matrox card it should work) I would buy a cheap Radeon X1xxx card and get that one to work. You don't need the proprietary drivers for that cards because even 3D- and X-Video-acceleration is supported by the radeon driver. The bonus is it don't suffer of the performance problems under KDE4 as those proprietary ones from nVidia (your FX5500 isn't supported by the latest version 180 anyway).

C]-[aoZ

P.S.: Please always take in mind that using two displays with different resolutions is likely to be a non-out-of-the-box mechanism. So if it doesn't work at first glance don't give up and ask again.

---


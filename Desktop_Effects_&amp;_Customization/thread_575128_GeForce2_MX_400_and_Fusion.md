---
title: "GeForce2 MX 400 and Fusion"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by mmtowns on 2007-10-13
I found some success today installing Compiz Fusion, so I thought I would share it with anyone else who may find it useful.

Here's are my system specs:
AMD Athlon 1700XP
Nvidia GeForce2 MX 400
1.4 GB RAM
Ubuntu 7.04

First, enable the restricted driver...
System -> Administration -> Restricted Drivers Manager

Reboot when it says to do so.

Follow the tutorial from [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

Finally, use this page with help configuring Fusion:
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Thanks to forum member, dmber, for the help!

The only issue I've had are disappearing title bars from time to time.  Restarting fusion seems to be a temp. fix.  I haven't tried the suggested 

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

...yet, but that could help others who might have the same issue.

---

### Post by darkazurka on 2008-05-30
(I'm using Geforce2 MX 400)
I'm a Hardy Heron user (after I upgraded from Gutsy to Hardy). In the beginning of using Gutsy, window decoration worked when having desktop effects on. Then(!).. after a bit of time on Feisty, either I put window decoration on or off, didn't matter, there was no functioning window decoration . 

Window decoration is the bar above window which have three buttons on top right A)Minimize B)Maximize C)Close

When I upgraded to Hardy, no change occured. It still doesn't matter if I put window decoration plugin on or off, no window decoration happens.

---

### Post by darkazurka on 2008-07-03
I solved my issue! It was as simple as installing xserver-xgl, logging out... and logging in!
I got a black white screen at login which freaked me out(!) but it appears it was just a preloading. Yay! :)

...but :( ...checking the [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager) > XGL is not recommended as upstream is moving towards a complete Xorg replacement.
I'll uninstall xgl. I've also changed video card to nvidia NV44A [GeForce 6200] , and I think it will just be the same result.

---


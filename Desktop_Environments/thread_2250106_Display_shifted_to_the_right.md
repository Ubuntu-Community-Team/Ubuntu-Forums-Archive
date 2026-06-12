---
title: "Display shifted to the right"
date: 2014-10-26
forum: Desktop Environments
---

### Post by ninfomane2 on 2014-10-26
Hi all !

I just install Xubuntu 14.04 on a mediacenter (Intel Atom) but the display is shifted to the right.
I have a black strip on the left and the right of the screen is hidden.

I read many forum threads explaining how to solved the problem. They're all old threads (few years and older version).
The display settings only allow me to select 60Hz. I don't have a file ~/.config/monitors.xml and create an xorg.conf file didn''t work either.
I plug a LED TV 1920x1080p by VGA.

I'd really appreciate some help for this issue. Thanks !

---

### Post by ninfomane2 on 2014-10-27
When I boot in recovery mode and then resume to normal boot, nothing else done, the screen is well centered.
If I boot directly to normal mode, the screen is then shifted to the right.

I guess it's the X autoconf which not detected properly the TV or the Integrated GPU.

Someone can give me a tips to get further ?
Thanks.

[EDIT] I also try another resolution. First with 1920x1080 (native resolution of the TV), the screen is shifted on the right. Then 1280x720 but the screen is shifted on the left. With 1280x1024, the screen is well positionned but the picture looks flatten...

---

### Post by ninfomane2 on 2014-10-29
Alright,

After a complete reinstall of Xubuntu and a deep search in my TV menu, I find the option to auto adjust position screen and works fine now.

[EDIT]
I still want to know why I needed a such trick to get my screen displays properly.
Don't hesitate to give more information.
Thanks.

---


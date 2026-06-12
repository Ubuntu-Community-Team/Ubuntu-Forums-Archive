---
title: "Retroarch KMS mode help?"
date: 2015-07-03
forum: Emulators
---

### Post by Dylstew on 2015-07-03
[SIZE=2][FONT=arial]Retroarch has a feature that uses KMS to achieve low input latency.
[https://github.com/libretro/RetroArch/wiki/KMS-mode](https://github.com/libretro/RetroArch/wiki/KMS-mode). I have an Nvidia card and Nouveau has support for it so I hope it works with my card.

First , I need to install the required Mesa, [COLOR=#333333]libgbm and [/COLOR][COLOR=#333333]libdrm.
Thing is, I'm a total newbie to Ubuntu so I have no idea how. I've already installed Retroarch itself with some terminal commands I found on the internet, and the thing itself is working.

Then, I need to get the input working outside of X. (as far as I know, going outside of X is ctrl+alt+f1 right?)

[/COLOR][https://github.com/libretro/RetroArch/wiki/Input-drivers-in-Linux-without-Xorg.]("https://github.com/libretro/RetroArch/wiki/Input-drivers-in-Linux-without-Xorg")

[COLOR=#333333]For that I need Libudev and libxkbcommon. Then I need to setup udev permissions by making the file by making a file, putting something in it and running two commands.

Once that is all done, how do I make sure Retroarch turns on KMS?

And, how do I get my PS3 controller working in Retroarch in general?

edit: Someone on another forum helped me, it worked but..well, it made no difference. Huh?

[/COLOR][/FONT][/SIZE][COLOR=#333333][FONT=Helvetica Neue][SIZE=2][FONT=arial]
[/FONT][/SIZE]
[/FONT][/COLOR]

---


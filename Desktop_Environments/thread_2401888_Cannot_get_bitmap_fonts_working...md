---
title: "Cannot get bitmap fonts working.."
date: 2018-09-24
forum: Desktop Environments
---

### Post by zhangweiwu on 2018-09-24
In the past, enabling bitmap is as easy as linking 70-force-bitmaps.conf in /etc/fonts/conf.d while removing any references to 70-no-bitmaps.conf

Since 18.04 however, this would not give the user all bitmap fonts. The only fonts that appear in fc-cache(1) with this technique are Fixed, Unifont, Wqy-Bitmap. All of the typical ones like Helvetica, Times, Lucida would not show up.

Since Fixed, Unifont, Wqy-Bitmap are all typical fonts used in a terminal emulator and "Helvetica, Times, Lucida" all do not fit terminal emulators, I have the impression that 18.04 only wants terminals to use Bitmap fonts, by design.

Any hint?

P.S. If course I ran `sudo dpkg-reconfigure fontconfig`

---

### Post by zhangweiwu on 2018-10-07
I took this problem to font-config list and got no answer there either:

[https://lists.freedesktop.org/archives/fontconfig/2018-October/006341.html](https://lists.freedesktop.org/archives/fontconfig/2018-October/006341.html)

---

### Post by zhangweiwu on 2018-10-25
The cause is found. I should have installed xfonts-100dpi but I installed xfonts-100dpi-transcoded instead.

---


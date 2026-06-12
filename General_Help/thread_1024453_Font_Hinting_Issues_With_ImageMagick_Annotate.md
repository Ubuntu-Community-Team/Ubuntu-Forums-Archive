---
title: "Font Hinting Issues With ImageMagick Annotate"
date: 2008-12-29
forum: General Help
---

### Post by gummy182 on 2008-12-29
I recently performed a complete site migration from a CentOS server to a new Hardy box. This was my first time setting up an Ubuntu environment. After (seemingly) getting everything running on the new machine, I noticed that fonts rendered using RMagick/ImageMagick were not the same or as nice on the Ubuntu server. Certain parts of characters appear distorted/clipped or smoothed too much by antialiasing.

I've tried googling for solutions to this problem, ranging from *dpkg-reconfigure fontconfig-config* to enabling *TT_CONFIG_OPTION_BYTECODE_INTERPRETER* and compiling freetype from source, but nothing seems to have an effect.

Here is a comparison between how the old CentOS server handled ImageMagick annotations vs. the new Ubuntu server:
[IMG]http://i5.photobucket.com/albums/y151/gummy182/comparison.jpg[/IMG]
(Note the unusable/unbearable 'H')

Both servers are running ImageMagick 6.4.4

If anyone could help me with this problem I would greatly appreciate it. Thanks!

---


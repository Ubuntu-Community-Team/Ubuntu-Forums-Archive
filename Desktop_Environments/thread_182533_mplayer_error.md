---
title: "mplayer error"
date: 2006-05-26
forum: Desktop Environments
---

### Post by morequarky on 2006-05-26
New_Face failed. Maybe the font path is wrong.  Please supply the text font file (~/.mplayer/subfont.ttf).

This is strange.  As far as I know mplayer works fine.  Why does it keep giving me this error?

---

### Post by 3rdalbum on 2006-05-26
There's a package called mplayer-fonts, which you need to install in order to get rid of the error. I think it's because MPlayer likes to use its own custom font to render some of the track information and things.

The package is in repositories and I think it's called mplayer-fonts... but don't quote me on that (running Windows ATM so I can't check)

---

### Post by sYs^ on 2006-05-26
I use 'msttcorefonts' to render subtitles. (sudo apt-get install msttcorefonts) and the location of the fonts is: /usr/share/fonts/truetype/msttcorefonts/ .

---


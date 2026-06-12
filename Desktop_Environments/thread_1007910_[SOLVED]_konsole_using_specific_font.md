---
title: "[SOLVED] konsole: using specific font"
date: 2008-12-10
forum: Desktop Environments
---

### Post by phorminx on 2008-12-10
My favorite font is
-misc-fixed-medium-r-normal-*-20-*-*-75-*-*-*-*
I know it's not scalable and it doesn't give me bold or slanted. Yet I just like it better than any other font. Is it possible to teach konsole to use it? I've played with ~/.fonts.conf and fc-cache. But either these are the wrong tools for that, or I have not yet figured out how  to do it right: when I use systemsettings to check the available fonts ("general" or "fixed width") they do not show my font. Any hints are appreciated!

---

### Post by phorminx on 2008-12-13
Well, I learned that this has nothing to do with konsole or kde. But it's all about fontconfig. So to get bitmap fonts for applications like konsole and gnome-terminal, I replaced in /etc/fonts/conf.d the link for 70-no-bitmaps.conf with 70-yes-bitmaps.conf (both of these files actually reside in /etc/fonts/conf.avail), ran `fc-cache -fv', restarted X and got all the fonts I want. (Yes, everything you need is already available, that's nice!)

Somehow, some of the bitmap fonts seem to be better optimized for their actual size than the scalable fonts (which is no surprise when you think about it...).

---


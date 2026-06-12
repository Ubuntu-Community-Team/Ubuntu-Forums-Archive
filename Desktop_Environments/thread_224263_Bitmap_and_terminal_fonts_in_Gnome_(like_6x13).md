---
title: "Bitmap and terminal fonts in Gnome (like 6x13)"
date: 2006-07-27
forum: Desktop Environments
---

### Post by wildutah on 2006-07-27
This has been answered before here, but I wanted to add a few keywords so that searchers could find the solution.  If you need to use the font "fixed" or "6x13", you need this solution.

6x13 is a carefully designed terminal font that has been one of the most popular unix fonts for decades.  It widely considered the most readable fixed font of its size.  Today it supports one of the fullest quality unicode character sets as well as old encodings.

But Gnome doesn't allow you =; to select it from font selection menus.  Gnome doesn't think you should be using terminal fonts for some reason.  So you need to fix the settings to allow the use of common fonts like this.

run
>sudo dpkg-reconfigure fontconfig

Don't worry.  You can't screw up anything using this program that you can't fix by simply running it again.  When it asks if you want bitmapped fonts, just day yes.  6x13 will show up as Fixed, SemiCondensed, 10 point.  Other great terminal fonts may how up under "Fixed" and "Terminal."

Terminal users, remember!  Dapper has all its charsets set to UTF8 so you will be disappointed with non-unicode terminals like rxvt and Eterm (unless you have recompiled unicode versions).  gnome-terminal works fine and the repositories include a unicode rxvt.  6x13 supports unicode.

Other fine fonts like 7x14 can also be used this way.

---

### Post by john5704 on 2008-02-13
Has anyone been able to get 7x14 ?  I've tried Fixed, MiscFixed, and Terminal but it either looks like 6x13 or some other font.

---

### Post by puntium on 2008-05-12
Check out this tip:

[http://www.ubuntutips.net/search/node/6x13](http://www.ubuntutips.net/search/node/6x13)

---


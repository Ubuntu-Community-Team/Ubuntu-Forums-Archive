---
title: "Fonts in Lucid Lynx"
date: 2010-05-07
forum: Desktop Environments
---

### Post by silv3rm00n on 2010-05-07
Hi

In KDE :
I upgraded my system from 9.10 to 10.04.
I see some difference in fonts. In Karmic fonts were slightly smaller and they are around 20% bigger in Lucid for the same font size.

In Karmic I used the xml file shown in 
[https://wiki.ubuntu.com/Fonts]("https://wiki.ubuntu.com/Fonts")

and fonts appeared very good.

But after upgrading to Lucid they appear little bigger.

Moreover fonts like Arial and Verdana dont appear in proper shapes
[IMG]http://img532.imageshack.us/i/fontfb.png/[/IMG]

Image Link >> [http://img532.imageshack.us/i/fontfb.png/](http://img532.imageshack.us/i/fontfb.png/)

How do I render the Arial font properly? How to make the rest of the fonts look proper?

In GNOME playing with the antialiasing settings does the job fine. How to fix in KDE ?

Thanks
Silver

---

### Post by Zorael on 2010-05-08
I think "playing with antialiasing" (in GNOME) should be the same as setting Use antialiasing: true, then going into Configure, checking Use sub-pixel rendering (RGB), and selecting Hinting style: Full. Beware that it *will* recreate your current **~/.fonts.conf** file and flatten your hierarchy and neat comments, so back it up first.

Those fonts settings (at the wiki page you linked to) add quite a bit of complexity, so I'm not quite sure what's happening to your Arial. It doesn't look like Arial to begin with, and it seems to only have light hinting, or perhaps it's being auto-hinted.

To begin with check if it's being mapped to something else.
```
$ fc-match Arial
Arial.ttf: "Arial" "Normal"
```

Aside from that I'd just try to selectively comment sections out of the .fonts.conf file and iteratively track down what could  cause the behavior. Changes will only affect newly started programs.

---


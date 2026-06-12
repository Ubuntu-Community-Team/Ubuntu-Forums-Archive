---
title: "GTK Font size too big.."
date: 2009-05-12
forum: Desktop Environments
---

### Post by Naatan on 2009-05-12
I have Ubuntu 9.04 with Kubuntu installed on top of it.

When running a GTK app the font size is much bigger than my KDE font size, I tried decreasing the font size manualy under System Settings > Appearance > GTK Styles and Fonts, but the font size remains unchanged (also after rebooting).

Anyone know what I might be able to do about this?

And while I'm at it, is there any way I can make Dolphin the default file manager when opening a file manager from within a GTK app? (eg when you right click > open directory on a download in firefox).

---

### Post by days_of_ruin on 2009-05-12
In a terminal:
```
gconf-editor /desktop/gnome/interface/font_name
```

What size does it say?

---

### Post by Naatan on 2009-05-12
Sans 8, but I'm pretty sure my GTK font size is larger than that.

---

### Post by t0mppa on 2009-05-22
Had the same problem here and going to System settings / Appearance / Fonts and setting Force fonts DPI to 96 DPI finally decreased the GTK apps's fonts to a more reasonable size.

---

### Post by bhadotia on 2009-06-26
> **t0mppa said:**
> Had the same problem here and going to System settings / Appearance / Fonts and setting Force fonts DPI to 96 DPI finally decreased the GTK apps's fonts to a more reasonable size.

Thanks dude, I was just wondering how to do that now, without the gtk style and fonts system setting module in Appearance.

---

### Post by ario on 2009-11-16
Thanks a lot days_of_ruin.
My problem was that all texts in ubuntu studio 9.10 was very small for me to read them.
I went to where you said and changed all font sizes from 8 to 12 so texts are no big enough for me to read them easier than before. It solved my problem.:D

---

### Post by urbanus on 2010-04-30
THANK :-)

A simple solution toa annoying problem that I would never have thought of / stumbled upon myself :-S

---

### Post by Geremia on 2012-12-24
> **t0mppa said:**
> Had the same problem here and going to System settings / Appearance / Fonts and setting Force fonts DPI to 96 DPI finally decreased the GTK apps's fonts to a more reasonable size.Thanks
That fixed the problem for me.

---

### Post by overdrank on 2012-12-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


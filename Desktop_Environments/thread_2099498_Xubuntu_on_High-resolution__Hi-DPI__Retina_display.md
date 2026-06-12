---
title: "Xubuntu on High-resolution / Hi-DPI / Retina display"
date: 2012-12-29
forum: Desktop Environments
---

### Post by ksatta1 on 2012-12-29
I've been tweaking Xubuntu on my Macbook Pro 15" Retina display and now only two things remain:
- The Window Buttons in the panel are too narrow, there seems to be a hardcoded maximum? Also if I increase the panel size to 50 or more then that just add rows instead of increasing the buttons' height.
- The icons in the indicator plugin are too small. They seem to stop growing after panel size 49 even though they are scalable vector graphics. And also it just adds rows when setting a higher size for the panel.

Anyway I thought I'd check if I'm missing some setting before filing a feat. req. / bug report.

So far I've done the following:
- Settings / Appeareance / Fonts / Custom DPI 220
- In Firefox about:config I've set "layout.css.devPixelsPerPx" to "2"  (NOTE: This seems to work just like in OS X, the text is still rendered at the high resolution, but pages' layout is scaled so that everything looks OK).
- Cursor size max
- Panel size 49.

I'm quite happy with the current setup, but one can never tweak too much :)

---

### Post by Andy45 on 2012-12-30
Have you tried tweak resolution in Settings-->Displays?

---

### Post by ksatta1 on 2012-12-30
> **Andy45 said:**
> Have you tried tweak resolution in Settings-->Displays?

I've set it to the max (2880x1800), so that text and images look crisp. But that also causes the two remaining problems mentioned in the first post.

Thanks for the suggestion though :)

---

### Post by Rocklobster690 on 2013-01-06
Can you please port a screenshot of Xubuntu on Retina. Sounds AWESOME.

---

### Post by ksatta1 on 2013-01-07
Yeah, it's quite awesome :D Soon I should receive my 16 euro usb wifi adapter and then the WiFi should work too (now it disconnects sometimes).

Screenshot (obviously you need a high res display to see how awesome it is :) ) : [http://imageshack.us/photo/my-images/708/screenshot0107201307285.png/](http://imageshack.us/photo/my-images/708/screenshot0107201307285.png/)
(Left-click the image first, then right-click save as.. and open the file to get the full res)

> **Rocklobster690 said:**
> Can you please port a screenshot of Xubuntu on Retina. Sounds AWESOME.

---

### Post by ksatta1 on 2013-04-18
To get bigger radio buttons and checkboxes in Firefox, xfce menus etc (in Greybird theme for example):
/usr/share/themes/Greybird/gtk-2.0/gtkrc:
Change GtkCheckButton::indicator_size = 30

Figured that one out from [http://ubuntuforums.org/showthread.php?t=954607&p=6066698#post6066698](http://ubuntuforums.org/showthread.php?t=954607&p=6066698#post6066698) .

Now this is much better :)

EDIT: or copy the whole theme dir to ~/.themes and modify there (that's what I did).

---


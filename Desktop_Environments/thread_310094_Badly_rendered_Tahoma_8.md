---
title: "Badly rendered Tahoma 8"
date: 2006-11-30
forum: Desktop Environments
---

### Post by nicolas314 on 2006-11-30
I am having trouble configuring my fonts in Ubuntu, have had the same problem with Dapper and Edgy. I spend the day working on an Ubuntu laptop that can render Tahoma 8 perfectly in the Windows way: no anti-aliasing so no strain on the eyes. At home it seems I cannot reproduce this, though I have tried everything I could. Tahoma 8 is completely blurry (very hard on the eyes) with anti-aliasing turned on, and completely jaggy (almost illegible) with anti-aliasing turned off. Here is my home configuration:

19 inch screen, 1280x1024, configured for 96 dpi both in X and gnome-font-settings
Gnome font settings: I have tried all possible combinations for Font Rendering, Smoothing, Hinting, but in all cases Tahoma 8 does not render correctly: either blurry or absurdly jaggy (letters look like bugs).

The only difference I can think of is the screen size. I have tried booting X with different dpi resolutions or modifying the system resolution in gnome-font-settings, but this does not improve the fonts. Why does Tahoma 8 refuse to render correctly (i.e. without anti-aliasing) on this machine?

Any help appreciated.

---

### Post by 23meg on 2006-11-30
Is your home screen a CRT? If so, size isn't the only difference.

It will also help if you post screenshots.

---

### Post by nicolas314 on 2006-11-30
Home screen is LCD, 19".
Attached is a screenshot of Tahoma 8 with anti-aliasing switched off and autohinting switched on. Check out the 'x' in "Subpixel (LCD's)" or the 'u' in "Full", they are beyond jaggy, there are obvious rendering issues there.

Thanks for helping

---

### Post by nicolas314 on 2006-11-30
Replying to my own question... I have found the following thread quite helpful:
[http://www.ubuntuforums.org/showthread.php?t=208396&highlight=firefox+fonts](http://www.ubuntuforums.org/showthread.php?t=208396&highlight=firefox+fonts)

I also noticed that the Tahoma files I was using (taken from a Win2k box) were about 30% smaller than other ones I found on a WinXP box. Upgrading the files and re-building the font cache helped a lot. Now the results are much better without anti-aliasing, at least the fonts are legible. Not perfect yet, but a real improvement!

Now I still have to understand why certain characters still refuse to render correctly like '2' and '8', and why Firefox/Thunderbird seem to behave differently than the rest of Gnome...

---

### Post by blackmh on 2006-12-01
Try this, works excelent 
[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by rhussa on 2006-12-06
Try this! this has done amazing font display;
[http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/](http://jaganath.wordpress.com/2006/07/16/ubuntu-install-log-6-finally-os-x-like-font-rendering-in-linux/)

---


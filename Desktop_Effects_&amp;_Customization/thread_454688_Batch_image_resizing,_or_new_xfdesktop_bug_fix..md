---
title: "Batch image resizing, or new xfdesktop bug fix."
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by drpynchon on 2007-05-25
Hey folks, another recent convert here, to xubuntu in particular and am in love. One problem though: I overeagerly upgraded my system to xfce 4.4.1 and have run into an issue with desktop backgrounds. I seem to no longer have the option of zooming images to fill the screen as I once did. I think this was a limitation on older versions of xfdesktop which was fixed, but it's come back for reasons that are beyond me. In any event, I was hoping someone had an obvious fix for this.

If not, I was hoping for a workaround as follows: I have a huge pool of images in jpg format that I cycle through as backgrounds. They are of varying dimensions, and I'm obsessed with not altering the aspect ratio on them or having borders on my desktop wallpaper, so that's why the zoom feature is useful. Is there a way to batch transform these images to a MINIMUM resolution of 1680x1050 (my WSXGA+ screen), and have at least one of the dimensions equal my screensize? I've been playing around with ImageMagick and I haven't quite figured out a trick to do this.

For example, a combination of "-resize '1680x<' -resize 'x1050<'" would work but only on images where at least one dimension is less than the final dimension.

Any ideas or programs I haven't run into yet?

---

### Post by vjones777 on 2007-12-09
Found a couple of posts that might help this issue

[A script that might be modified ]("http://ubuntuforums.org/showthread.php?t=403147")
[Some other options]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=207675&page=2")
The second post suggests a couple of ways...
[LIST]
[*]image magick with the nautilus extension.
[*]Gwenview (KDE)
[*]phatch
[/LIST]

Hope that helps others.

---

### Post by stani on 2007-12-09
Try phatch (PHoto bATCH processor) which has a nice user interface for it. There is a deb installer for Ubuntu:
[http://photobatch.stani.be](http://photobatch.stani.be)

---


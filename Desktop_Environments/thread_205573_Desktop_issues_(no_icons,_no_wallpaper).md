---
title: "Desktop issues (no icons, no wallpaper)"
date: 2006-06-28
forum: Desktop Environments
---

### Post by nmsmith on 2006-06-28
[LIST=1]
[*]Some time ago, I removed nautilus's desktop icons, as recommended by the FAQ on the conky web page. I now feel like I would like them back as I have stopped using conky. In gconf-editor I have checked "show_desktop" in apps>nautilus>preferences but have no icons.

What to do?


[*]Now Gnome appears to have stopped displaying the wallpaper. This happened while I was installing compiz and xgl, although I can't say which exactly did it! If I open the wallpaper utility the background reappears before I even have to reselect it, but it has always gone next time I log on.

What to do?


[*]On a slightly less related point, has anyone noticed that ```
feh -ZF
``` doesn't work in Dapper as it did in Breezy? The gnome panels still appear even though I have told feh to be in full screen mode. Also using compiz using feh in window mode results in a pulsating image window, which is pretty useless. Can this be helped?
[/LIST]

Thanks

---

### Post by knn on 2006-06-28
[QUOTE=nmsmith][LIST=1]
[*]Some time ago, I removed nautilus's desktop icons, as recommended by the FAQ on the conky web page. I now feel like I would like them back as I have stopped using conky. In gconf-editor I have checked "show_desktop" in apps>nautilus>preferences but have no icons.

What to do?


[*]Now Gnome appears to have stopped displaying the wallpaper. This happened while I was installing compiz and xgl, although I can't say which exactly did it! If I open the wallpaper utility the background reappears before I even have to reselect it, but it has always gone next time I log on.

What to do?


[*]On a slightly less related point, has anyone noticed that ```
feh -ZF
``` doesn't work in Dapper as it did in Breezy? The gnome panels still appear even though I have told feh to be in full screen mode. Also using compiz using feh in window mode results in a pulsating image window, which is pretty useless. Can this be helped?
[/LIST]

Thanks[/QUOTE]

While installing compiz you probably changed your session and it doesn't load nautilus on logon. Login, load nautilus (if you start it as a file browser it should also start as the desktop),  and save your session.

---

### Post by nmsmith on 2006-06-29
Thanks that worked perfectly. Is there a way to save the session without checking "save automatically" in the session settings?

And how about the feh issue? Am I the only one who has noticed it, on two different machines?

---

### Post by knn on 2006-06-29
[QUOTE=nmsmith]Thanks that worked perfectly. Is there a way to save the session without checking "save automatically" in the session settings?

And how about the feh issue? Am I the only one who has noticed it, on two different machines?[/QUOTE]

AFAIK there's no other way, since Ubuntu uses a custom logout window, which does not have that feature

---

### Post by nmsmith on 2006-06-29
Okay cheers, for expediency's and elegance's sake I was just making sure that I hadn't been unnecessarily doing things the long way.

---


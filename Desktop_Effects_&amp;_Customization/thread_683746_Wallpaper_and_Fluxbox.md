---
title: "Wallpaper and Fluxbox"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by rogers45 on 2008-01-31
How to keep the wallpaper in fluxbox? every time I sign off and signing on again the wallpaper i've chossen keeps disappearing. Why is that?

---

### Post by kerry_s on 2008-01-31
did you add it to your startup? there should be a example in there.
[http://fluxbox-wiki.org/index.php/Howto_set_the_background](http://fluxbox-wiki.org/index.php/Howto_set_the_background)

---

### Post by urukrama on 2008-01-31
If you set the wallpaper with Feh, add this to your startup file:

> eval `cat $HOME/.fehbg` &

If you use Nitrogen, add this:
> nitrogen --restore &

If you use fbsetbg, see the link kerry_s gave.

If you use other applications (see [here]("http://urukrama.wordpress.com/2007/12/05/desktop-backgrounds-in-window-managers/") for various options) you can use the code you use to set the background (for example "hsetroot -fill /path/to/image")

---

### Post by rogers45 on 2008-02-01
Thanks this is Solved! And i have to set "fbsetbg -l"

---


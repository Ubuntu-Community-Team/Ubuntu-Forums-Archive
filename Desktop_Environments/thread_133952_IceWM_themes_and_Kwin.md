---
title: "IceWM themes and Kwin"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Mr. Swiveller on 2006-02-21
Dear all,

I am having trouble getting IceWM themes to work with Kubuntu (Breezy Badger release). The 'IceWM theme' option doesn't show up in the 'window decorations' section of Kcontrol, regardless of whether I run it as root or not . 

While it is possible to run IceWM in conjunction with Kicker, I'd really like to be able to use the IceWM themes and still get the additional Kwin features. Is there anyone who knows what might be wrong with my setup?

Many thanks in advance!

Cheers,

Swiveller

---

### Post by Jucato on 2006-02-21
Unfortunately, I don't think this is possible. IceWM and KWin are two different window managers. You can't have both running at the same time. However, you can have KDE use IceWM instead of KWin as the window manager. I'm just not sure how to do this exactly. I think you can install the icewm packages from the repository, then when you login (in KDM), under the "Sessions" option, choose IceWM. Haven't tried it out so I'm not 100% sure.

Besides, what "additional Kwin features" are you after anyway? Who knows, they might not be KWin features but KDE features instead.

---

### Post by Mr. Swiveller on 2006-02-21
Dear Fenyx,

First of all, thank you for the tips. 

If I am not mistaken, iceWM themes support was introduced into KDE sometime after version 2.2. While I am not sure whether it is actually Kwin which handles the themes, it should be possible to select iceWM themes installed on a KDE box simply from the 'Window Decorations' menu.

Currently, when I want to run IceWM themes I launch an IceWM session and then execute Kicker from a terminal. While this generally works well, it does not give me support for things like dropshadows. Hardly crucial, I know, but I'd still like to try and get the more fancy stuff to work.


Cheers,

Swiveller

---

### Post by Adrian on 2006-02-21
Try installing the **kdeartwork** package.

---

### Post by Jucato on 2006-02-21
I'm not entirely sure how KWin can support the IceWM themes. probably you need something like deKorator or Crystal? I'm not really sure. I haven't installed kdeartwork also, so it might (or might not) solve the problem. Sorry I couldn't be of more help. :)

Just found this page, don't know how much it will help:
[http://www.barbarakaemper.de/en/bk_en_desktop_themes_icons_wallpaper_install_kde.htm]("http://www.barbarakaemper.de/en/bk_en_desktop_themes_icons_wallpaper_install_kde.htm")

---

### Post by Adrian on 2006-02-21
Installing **kdeartwork** should be enough. Then "IceWM" will appear in the Window Decoration drop down menu.

I'm currently using [this]("http://www.kde-look.org/content/show.php?content=27090") IceWM theme. Looks neat together with my "Gnomified" icons :)

---

### Post by Jucato on 2006-02-21
cool! Thanks Adrian! something new I learned today! :D

(mavvert-icewm window decorations + GNOME-mix icons right?)

---

### Post by Adrian on 2006-02-21
> (mavvert-icewm window decorations + GNOME-mix icons right?)

(Correct. My desktop looks more or less the same as the first Gnome-mix screenshot. The only thing I don't really like is that the Kmenu is represented by a Gnome foot (I mean, it is actually KDE and not Gnome). Not difficult to fix, though.

I've always liked the Gnome look, so this solution gives me the best of both worlds, so to speak  :) )

---

### Post by Mr. Swiveller on 2006-02-21
Thank you for the help guys! I will try Adrian's solution as soon as I'm on my Linux box. 

(And yes, that theme DOES look cool!)

Cheers,

Swiveller

---

### Post by Mr. Swiveller on 2006-02-21
I installed the 'kdeartwork-theme-window' package, and it all works blissfully!

Thanks!

Swiveller

---


---
title: "Menu background image?"
date: 2011-04-03
forum: Desktop Environments
---

### Post by adamluck on 2011-04-03
I was wondering if it is possible to use a custom background image for the background of the [Applications Places System] menus and also behind the system clock & other things along the top bar.  I have set the panel backgrounds to a certain image and would like to sync them so that the entire panel and menu areas have the same background.  I've installed CompizConfig Settings Manager and haven't been able to find anything pertinent inside it and I haven't been able to find much in Google...

---

### Post by Krytarik on 2011-04-03
As for the panels, please see me earlier post:
[http://ubuntuforums.org/showthread.php?p=10622129#post10622129](http://ubuntuforums.org/showthread.php?p=10622129#post10622129)

You can set a custom menu background like below, the example is again Maverick's Ambiance, add/modify the marked entries:

/usr/share/themes/Ambiance/gtk-2.0/gtkrc:
```
style "menu" = "dark" {
    xthickness = 0
    ythickness = 0

    bg[NORMAL] = "#43423f"
    bg[INSENSITIVE] = "#43423f"
    fg[INSENSITIVE]   = shade (0.54, "#43423f")

    engine "murrine"
    {
        roundness = 0
    }
[B][COLOR=Blue]
    engine "pixmap"
    {
        image
        {
            function         = BOX
            recolorable     = TRUE
            detail         = "menu"
            file         = "menu.png"
            border         = { 0, 0, 0, 0 }
            stretch         = TRUE
        }
    }[/COLOR][/B]
}

```Greetings.

---

### Post by adamluck on 2011-04-03
Thank you very much for your help!  With both your reply and a look at the post you linked to I was able to change the background images for my panels and menus.  However, I made the changes by just locating the image files, backing up the previous ones and replacing them with my desired images.

---

### Post by Krytarik on 2011-04-03
Yeah, for the panels you can do that. Although I would choose the other way, because you don't need to modify the theme each time you want to set another background.

As for the menu background, that depends of course on the used theme, for Ambiance there is no backaground image at all.

---


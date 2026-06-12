---
title: "Themes not conforming."
date: 2012-01-09
forum: Desktop Environments
---

### Post by godsgifttoearth on 2012-01-09
please see screenshot.

some of my applications are adhering to my GTK theme, others are not. how do i diagnose the problem?

second part, how do i make new windows open centrally on the screen, they're opening all over the place now and its very annoying.

thanks for your help :D

[IMG]http://img810.imageshack.us/img810/5921/screenshot100112031027.jpg[/IMG]

---

### Post by Toz on 2012-01-09
> **godsgifttoearth said:**
> please see screenshot.

some of my applications are adhering to my GTK theme, others are not. how do i diagnose the problem?
Maybe its just me, but I can't make out the theme difference in the screenshot. If you are using Xubuntu 11.10, make sure you are using a GTK3-compliant theme (greybird is one such theme). Which applications are not conforming to the theme properties?

> second part, how do i make new windows open centrally on the screen, they're opening all over the place now and its very annoying.
Go to Setting -> Settings Manager -> Window Manager Tweaks -> Placement tab and make sure that the "At the center of the screen" option is selected. Note: you may have to play around with the "Maximum size of windows to trigger smart placement" value to get all windows to comply.

---

### Post by kholis on 2012-01-10
> **godsgifttoearth said:**
> please see screenshot.

some of my applications are adhering to my GTK theme, others are not. how do i diagnose the problem?


Your theme doesn't have gtk3 theme support. So all your gtk3 apps use gtk engine default theme. Please use other theme such a greybird or make the gtk3 theme your self. :)

---

### Post by godsgifttoearth on 2012-01-10
THANKS!

i actually didn't realise this used GTK3!

well i feel silly now.

thanks for the quick replies.

---

### Post by cottfcfan on 2012-01-10
You can also add this repo to your sources:
```
sudo add-apt-repository ppa:webupd8team/themes
```
This will probably get you about 10 GTK3 themes.
Ambiance blue, anewstart & hope are my favourites.

---


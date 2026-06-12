---
title: "Compiz on Ubuntu 8.10 - Can't customize wallpapers on desktop cube sides"
date: 2008-12-12
forum: General Help
---

### Post by Zevin64 on 2008-12-12
Hi I recently upgraded to Ubuntu 8.10. I now notice that in Compiz settings for 'Desktop Cube' under the 'Appearance' tab there are only options for changing images on 'Cube Caps' and 'Skydome'. There seems to be no option for changing the wallpaper on the sides of the cube like there was before.

Some assistance please?

---

### Post by geirha on 2008-12-12
It shares some of the configuration of metacity (the window manager that's used when visual effects are turned off), so changing the background for metacity, changes the background for compiz as well. Go to System -> Preferences -> Appearance -> [Background] and change the background there.

---

### Post by fubbleskag on 2008-12-12
additionally, compiz will let you specify different wallpapers for each desktop via the wallpapers plugin, but it requires telling metacity not to draw your desktop - which will mean no desktop icons. I believe there is a patch for metacity floating around to fix that, though.

---

### Post by geirha on 2008-12-12
Oh hang on. It's nautilus (the explorer) that draws the background image and the icons. Metacity does the windows borders and such. Fubbleskag's suggestion still applies, but he/she also means nautilus instead of metacity. Sorry for the mix-up.

---

### Post by fubbleskag on 2008-12-12
wow, look at us go! lol

---

### Post by Zevin64 on 2008-12-13
lol, fixed thanks to both of you :)

---


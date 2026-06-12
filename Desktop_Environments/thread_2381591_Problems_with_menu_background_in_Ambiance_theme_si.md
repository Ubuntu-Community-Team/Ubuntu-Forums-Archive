---
title: "Problems with menu background in Ambiance theme since upgrade to 17.10"
date: 2018-01-02
forum: Desktop Environments
---

### Post by mlgdr on 2018-01-02
Hi all,

after my upgrade to 17.10 it seems that some applications display menus with a light color an a white background instead of the dark (brown) background. One example is the editor "geany". As you can see from the screenshot, the inactive menu entries are readable whereas the active entries are displayed with a light text color on the gray background. Correct for the theme would be a dark background.
Interestingly, the menu background is correct, when I start Geany as root. This only happens, when I use the theme "ambiance". With "radiance" e.g. everything seem to be correct.

Any ideas what's wrong here?

---

### Post by mlgdr on 2018-01-03
The reason why the menus are displayed correctly when started as root, seems to be a different GTK version that is used when started with gksu. So it seems to be a problem with the Ambiance theme and the latest GTK version.

---


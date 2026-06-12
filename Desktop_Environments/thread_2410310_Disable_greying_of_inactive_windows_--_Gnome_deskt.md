---
title: "Disable greying of inactive windows -- Gnome desktop"
date: 2019-01-14
forum: Desktop Environments
---

### Post by shmu26 on 2019-01-14
I am on Ubuntu 18.10 with the default Gnome desktop.
When I display two windows side by side, the inactive one becomes slightly greyed or opaque.
For instance, if I am typing in a doc in LibreOffice, the PDF that is displayed in Document Viewer will become slightly greyed -- and it is more than slightly, if I enable a dark desktop theme, such as Yaru dark.

How to disable the greying behavior of inactive windows?

---

### Post by vanadium on 2019-01-14
How windows look when they are selected or not is defined by the theme. Either you need to use another theme, or edit an existing theme. Changing the theme unfortunately involves editing cascade style sheets (css). Not that difficult as such, but not straightforward either. A good general tutorial on how it works, i.e. one that involves copying part of the theme to a local folder so 1) you can make the changes as normal user and 2) the changes are not destroyed by a future update, [can be found here](https://blogs.gnome.org/mclasen/2014/05/06/tweaking-a-the-gtk-theme-using-css/).

---

### Post by shmu26 on 2019-01-14
Fair enough, so what item in the css do I want to edit?

After a little experimenting, it seems that Adapta and Adwaita don't grey out the application window, only the title bar, which is not a problem. 
Yaru standard greys the window a little, and Yaru-dark greys it a lot.

---


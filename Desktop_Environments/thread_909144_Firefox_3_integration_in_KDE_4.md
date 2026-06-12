---
title: "Firefox 3 integration in KDE 4"
date: 2008-09-03
forum: Desktop Environments
---

### Post by usien on 2008-09-03
Is there any progress in porting Firefox 3 to KDE 4. Whats the best way to integrate Firefox 3 in KDE 4?

---

### Post by sayakb on 2008-09-03
What problems are you facing? Is it the theme that is not coming up? If you want Firefox to have a theme with KDE4, in the Session properties, add **gnome-settings-daemon** to startup. Access Session properties thru Gnome by going to System->Preferences->Sessions

---

### Post by HTML-insane on 2008-09-10
Actually, I just did this:

```
sudo apt-get install gtk-qt-engine-kde4
```

Then went in system settings, "Appearance", then, "GTK styles and fonts".

---

### Post by Geoffrey on 2008-09-23
with gtk-qt-engine-kde4, the Qt4 theme is not well applied.

I found an Oxgen theme for GTK but does'nt work with qt-engine apparently

---


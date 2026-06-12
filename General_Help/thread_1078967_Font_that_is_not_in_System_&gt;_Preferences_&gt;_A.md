---
title: "Font that is not in System &gt; Preferences &gt; Appearance?"
date: 2009-02-23
forum: General Help
---

### Post by dorseye on 2009-02-23
Greetings,
I have been customizing my Ubuntu with new & different fonts. Most of the fonts can be easily changed in the menus: System > Preferences > Appearance, however I have a font that doesn't seem to want to update, which shows up by default under the Ubuntu text editor, and is also present in the Konversation menu (see attached image). It is big and I'd like to be able to size it down, but adjusting the font sizes in the aforementioned area does nothing. Where is this font size hidden?

---

### Post by Giant Speck on 2009-02-23
> **dorseye said:**
> Greetings,
I have been customizing my Ubuntu with new & different fonts. Most of the fonts can be easily changed in the menus: System > Preferences > Appearance, however I have a font that doesn't seem to want to update, which shows up by default under the Ubuntu text editor, and is also present in the Konversation menu (see attached image). It is big and I'd like to be able to size it down, but adjusting the font sizes in the aforementioned area does nothing. Where is this font size hidden?

I'm assuming you are using GNOME.  Konversation is a KDE application, meaning that its fonts, styles and colors are controlled separately from GNOME's settings.

I'm not sure if this will work, but try pressing Alt+F2 to bring up the run dialog and then enter "systemsettings."  System Settings is the KDE version of GNOME's system settings dialog.  There you should be able to change the fonts for KDE applications.

If that doesn't work, you can always do the same in qtconfig-qt4.  Just enter that command in the run dialog like you did systemsettings.

---


---
title: "Application font style in Ubuntu 12.04"
date: 2012-12-02
forum: Desktop Environments
---

### Post by gueygel on 2012-12-02
Hi everyone,

I messed up the whole font style used by applications on my system and I can't restore the defaults. This is the story:

I installed digiKam on a gnome desktop in Ubuntu 12.04. It didn't look well integrated and so I installed 'systemsettings', the KDE config editor, to be able to change the appearance of KDE applications.

After playing with the themes, styles and font settings I got what I wanted (which was mainly changing the color of the unreadable hover text), but then I realized that the font style and size in many applications (not all of them) such us Thunderbird, Firefox, Chromium, Texmaker... changed!!

I can't find a way to revert this situation. I found googling that in older versions of Ubuntu there was the "Application font" option in System>Appearance>Fonts, which I think it's exactly what I'm looking for, but I can't find it in 12.04. I tried with gconf-tools, dconf-editor, ubuntu-tweak... no success.

Does anyone know how to change the font style that applications like Firefox or Thunderbird use in Ubuntu 12.04?

Thanks!

---

### Post by gueygel on 2012-12-03
Ok, I managed to fix it.

Installing all the KDE settings stuff and playing with it created the hidden file 

~/.fonts.conf

That config was overriding the gnome font settings and thus changing the 'default font' in gconf-editor didn't have any effect. Removing that file did the trick.

---

### Post by Frogs Hair on 2012-12-03
Firefox and I think Tbird have font settings in preferences. If you are using Ubuntu not KDE the gnome teak tool is helpful.

---

### Post by gueygel on 2012-12-04
Yes, both applications have their own font settings, but modifying this didn't have any effect either (well, in Thunderbird yes, you could modify the font style of body text inside messages, but not the font style used in the GUI!).

---


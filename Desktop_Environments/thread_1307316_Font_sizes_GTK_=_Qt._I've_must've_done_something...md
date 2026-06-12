---
title: "Font sizes: GTK /= Qt. I've must've done something..."
date: 2009-10-31
forum: Desktop Environments
---

### Post by kelvin.illa on 2009-10-31
My VLC player had a bigger font size after I rebooted. Since I knew that VLC uses Qt, I installed the Qt config tool to see what's wrong. Though the settings were unchanged -- the default Qt setting is set to Desktop settings, the font sizes are still the same (10 for GTK, 10 for Qt) -- the Qt font is actually two points larger than my GTK font (i.e., the size 10 in my GTK is actually 12 in Qt).

Is there a way to fix this?

The last thing I remember doing that might (or might not) have caused this was using the 'Computer Janitor (Karmic version).'

---

### Post by kelvin.illa on 2009-10-31
Nevermind...

I solved it by using "GTK+" for the Qt GUI style setting rather than "Desktop Settings (Default)." I probably corrupted some configs.

---


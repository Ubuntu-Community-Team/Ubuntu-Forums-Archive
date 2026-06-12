---
title: "Changing the Unity panel name?"
date: 2013-06-15
forum: Desktop Environments
---

### Post by GreatEmerald on 2013-06-15
I need to change the "Ubuntu Desktop" name that appears every time there is no program running on Unity. There has been a suggestion on Ask Ubuntu about that: [http://askubuntu.com/questions/140742/how-do-i-change-the-desktop-name-on-the-unity-panel](http://askubuntu.com/questions/140742/how-do-i-change-the-desktop-name-on-the-unity-panel) However, the suggestion with *msgfmt* doesn't seem to work with 12.04. After doing that, the name stays as it was. In fact, it seems that changing locale files has no effect whatsoever (I can remove the unity.mo file from /usr/share/locale-langpack/lt/LC_MESSAGES while using the Lithuanian localisation, and Unity stays localised). Am I missing something here? Is there some update mechanism that has to be triggered in order for locale changes to take effect?

---

### Post by GreatEmerald on 2013-06-15
Oh, I figured it out. Apparently the file I'm supposed to be changing is in fact /usr/share/locale-langpack/lt/LC_MESSAGES/unity-2d.mo and not the regular "unity.mo" (at least when running Ubuntu through VirtualBox - it might be defaulting me to Unity 2D instead of 3D).

---


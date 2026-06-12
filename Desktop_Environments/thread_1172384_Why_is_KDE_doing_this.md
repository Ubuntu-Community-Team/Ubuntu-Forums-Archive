---
title: "Why is KDE doing this?"
date: 2009-05-28
forum: Desktop Environments
---

### Post by gymophett on 2009-05-28
I downloaded Compiz-Switch and emerald.
I put an Emerald theme up, didn't like it. Uninstalled emerald and Compiz switch. Now my windows won't take the KDE window decorations. It does some other. I don't know why. I can go to my system settings and Ozone is supposed to be my decoration. It makes me mad because I like the Ozone decoration. I log out, log back in, same thing. My web browser doesn't even have a Window Decoration! :o
Only some of my menus do.
What do I do?

---

### Post by chucky chuckaluck on 2009-05-28
> **gymophett said:**
> I downloaded Compiz-Switch and emerald.
I put an Emerald theme up, didn't like it. Uninstalled emerald and Compiz switch. Now my windows won't take the KDE window decorations. It does some other. I don't know why. I can go to my system settings and Ozone is supposed to be my decoration. It makes me mad because I like the Ozone decoration. I log out, log back in, same thing. My web browser doesn't even have a Window Decoration! :o
Only some of my menus do.
What do I do?

go to default applications and make sure that kwin is selected as window manager.

---

### Post by amadeus266 on 2009-05-28
Simple solution would be to reinstall compiz switch, then utilize it's menu to select different window decorator. I forget what the decorator for KDE is called since I use Ubuntu.

---

### Post by SunnyRabbiera on 2009-05-28
KDE4 and compiz dont really mix, hey not even KDE3 mixed with compiz.
Compiz is more of a gnome thing

---

### Post by NightwishFan on 2009-05-28
You can run this command to restore the kde window manager temporarily.
```
kwin --replace
```
To start it permanently, you just have to undo what you originally did. You can also add the 'kwin --replace' to the KDE autostart, and some versions of KDE have a window manager selection under the session settings.

---


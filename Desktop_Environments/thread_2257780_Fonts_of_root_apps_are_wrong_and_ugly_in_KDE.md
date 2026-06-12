---
title: "Fonts of root apps are wrong and ugly in KDE"
date: 2014-12-22
forum: Desktop Environments
---

### Post by kebabbaro on 2014-12-22
Hi everybody, with Kubuntu 14.04 LTS the fonts of applications started as root are wrong and ugly

wrong --> they are not the usual Ubuntu fonts, even if the right fonts are set in System Settings
I mean I started System Settings as root ( with kdesudo ), I tried to change the background color and indeed it worked: the background color was changed only for applications started as root.That confirms that System Settings running as root do work in changing setting for root applications.
So I checked again what were the fonts actually set, and everything is ok: the fonts set are exactly the same fonts set for non-root applications, i.e. ubuntu fonts.
So I really don't understand why the fonts used for applications run as root are not ubuntu :confused::confused:


ugly --> as you can see in the picture linked, when I try to select the ubuntu font systemwide, in the dialog window the font is rendered without the antialiasing correction
n

I am really puzzled, is this a bug or intendend behaviour? And most importantly: is there a way around that?

Thank you.


In the picture linked, the left window shows System Settings run as regular user, while the right window shows System Settings run as root. As you can see, the font settings are exactly the same. Also, the two dialog windows show that the ubuntu font is rendered without antialiasing when run as root (right window)

[http://postimg.org/image/mnpdd3dyz/](http://postimg.org/image/mnpdd3dyz/)

---

### Post by speartip on 2014-12-23
Hi Kebabbaro,

I has a similar problem when I first started using KDE.
What you need to do is go into system settings as root.
```
kdesudo systemsettings
```
There you can change the fonts, colour scheme, icons etc to match your user choice, in Application Appearance.
Hope this helps.

---


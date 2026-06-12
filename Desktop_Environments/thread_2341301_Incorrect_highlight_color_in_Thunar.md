---
title: "Incorrect highlight color in Thunar"
date: 2016-10-26
forum: Desktop Environments
---

### Post by eatmelast on 2016-10-26
Hello, I'm having a minor but annoying issue with Xubuntu 16.04. Hope someone can help me!

Basically, when highlighting something in Thunar, the selection rectangle is an ugly grey, irrespective of the color defined in "Highlight background" in the Theme Configuration settings. On the desktop, however, it displays correctly.

I've attached two images showing the difference between highlighting icons on the desktop vs. in Thunar.

[[IMG]http://en.zimagez.com/avatar/screenshot2016-10-2620-23-12.png[/IMG] Desktop]("http://en.zimagez.com/zimage/screenshot2016-10-2620-23-12.php")
[[IMG]http://en.zimagez.com/avatar/screenshot2016-10-2620-24-44.png[/IMG] Thunar]("http://en.zimagez.com/zimage/screenshot2016-10-2620-24-44.php")

---

### Post by CantankRus on 2016-10-26
Firstly, I would test in the guest account to determine if it is a user setting.
Looks to be a theme setting... testing the default greybird.
I would be looking for a value of "transparent" in the theme configs.

---

### Post by vasa1 on 2016-10-27
Both images posted by OP appear tiny :(

---

### Post by CantankRus on 2016-10-27
> **vasa1 said:**
> Both images posted by OP appear tiny :(
They're linked to 1.6mb zimages which display here.
Don't know why people link to such big images when attached images are adequate in most cases.

Anyway, the greybird theme has thunar specific settings in **/usr/share/themes/Greybird/gtk-2.0/apps/thunar.rc**.
If I change the name of the file so as it's not used....
```
sudo mv /usr/share/themes/Greybird/gtk-2.0/apps/thunar.rc /usr/share/themes/Greybird/gtk-2.0/apps/thunar.rc.bak
```
I get the highlight colour.
[ATTACH=CONFIG]271801[/ATTACH]
But the side pane background color also changes.

If you ran the previous** mv** command, use this command to move back...
```
sudo mv /usr/share/themes/Greybird/gtk-2.0/apps/thunar.rc.bak /usr/share/themes/Greybird/gtk-2.0/apps/thunar.rc
```
then comment out this section of **/usr/share/themes/Greybird/gtk-2.0/apps/thunar.rc** as shown...
[ATTACH=CONFIG]271802[/ATTACH]

---


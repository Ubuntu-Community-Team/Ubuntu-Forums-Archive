---
title: "Look of KDE apps in GNOME"
date: 2005-06-20
forum: Desktop Environments
---

### Post by sinbad782 on 2005-06-20
Hi, does anyone have any good tips on how to get a consistent look for KDE applications running under the GNOME desktop environment?

I have managed to get this working pretty well the other way around, but haven't heard of any corresponding techniques to acheive the opposite effect!

Thanks, PJS

---

### Post by miscz on 2005-06-20
Your best bet is Bluecurve theme, I find qt-gtk engines way too buggy.

---

### Post by byen on 2005-06-20
sorry this is not a solution ... but ive had a similar problem too ,so wanna chip in : all the kde applications in gnome menu do not have an icon....i mean they all have a similar ugly default no-icon icon. is there anyway to fix this?

---

### Post by YaAqoB on 2005-06-21
I installed K3b and that came with the nice Icon in the Gnome menu but then saying that Kcalc came with the boring default icon. 
Can we just edit the .desktop file and assign it a custom icon?

---

### Post by afonic on 2005-06-21
Yes if you edit the .desktop file you can add an icon.

Or better you can use the menu editor:

sudo apt-get install smeg

---

### Post by jonny on 2005-06-21
To get KDE apps looking respectable in Gnome, you need```
sudo apt-get kcontrol
```to install the KDE control centre.  Run it with```
kcontrol
```I chose a more suitable theme, made the colours a little more Human, turned on anti-aliasing, reduced the size of the display fonts, and selected the same typeface that Gnome uses.

I find it a little strange that ubuntu's default settings for KDE and Gnome are so different.

---

### Post by shakin on 2005-06-21
kde-look.org has a Kubuntu-Human theme.

[http://www.kde-look.org/content/show.php?content=21720](http://www.kde-look.org/content/show.php?content=21720)

---

### Post by Bandit on 2005-06-21
[QUOTE=miscz]Your best bet is Bluecurve theme, I find qt-gtk engines way too buggy.[/QUOTE]
I know what you mean there... Thats why I dont even right themes for the qt-engine.. 
Cheers,
Joey

---

### Post by byen on 2005-06-21
[QUOTE=afonic]Yes if you edit the .desktop file you can add an icon.

Or better you can use the menu editor:

sudo apt-get install smeg[/QUOTE]

"smeg" did the trick for me..thank you afonic.

---

### Post by afonic on 2005-06-22
[QUOTE=byen]"smeg" did the trick for me..thank you afonic.[/QUOTE]
 You're welcome.

I was extremely happy when I found it. Before I had to manually edit the .desktop file...

---


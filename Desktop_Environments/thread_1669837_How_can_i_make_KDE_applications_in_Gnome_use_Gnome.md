---
title: "How can i make KDE applications in Gnome use Gnome icons?"
date: 2011-01-18
forum: Desktop Environments
---

### Post by Macfunky on 2011-01-18
I run Gnome and i want KDE applications to use the same icon set as i have for my Gnome desktop. I have searched the file system and found a folder called "default.kde4" in /usr/share/icons. I assume this is where KDE applications pull their icons from. I have two questions -

Firstly, this folder is a linked folder. How do i find out where the original folder that it is linked to is?

Secondly, i am assuming, that the KDE icons won't be a name for name match for the icons i am using in Gnome (Faenza just in case anyone is curious). What is the easiest way to get the KDE icons changed for the one's i am using in Gnome?

---

### Post by youarefunny on 2011-01-24
> **Macfunky said:**
> I run Gnome and i want KDE applications to use the same icon set as i have for my Gnome desktop. I have searched the file system and found a folder called "default.kde4" in /usr/share/icons. I assume this is where KDE applications pull their icons from. I have two questions -
I would assume so (I don't do KDE).  I wish gnome had something like this (hint-hint any devs reading this).  Essentially it is a soft link to a icon theme folder.  So what you can do is just pull icons from it and your app will fit the current theme because when the theme changes this folder is linked to the current icon theme.
*(I think and assume, I'm not really sure.)*

> **Macfunky said:**
> Firstly, this folder is a linked folder. How do i find out where the original folder that it is linked to is?
In nautilus (default file manager for gnome) right click and click properties.  It should tell you the link target.  Or you can use the 'file' command.  

```
$file /usr/share/icons/default.kde4
/usr/share/icons/default.kde4: symbolic link to `oxygen'
```> **Macfunky said:**
> Secondly, i am assuming, that the KDE icons won't be a name for name match for the icons i am using in Gnome (Faenza just in case anyone is curious). What is the easiest way to get the KDE icons changed for the one's i am using in Gnome?
If your luck they might.  Try your luck and change the link to your favorite gnome theme. "ln -f /usr/share/icons/default.kde4 /usr/share/icons/THEME"  Unfortunatly you will need to change it every time you change your icon theme because gnome doesn't have the same feature.

Best of luck.

---


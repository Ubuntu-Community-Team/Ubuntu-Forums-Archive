---
title: "Changing icons on GNOME"
date: 2006-04-10
forum: Desktop Environments
---

### Post by Sushi on 2006-04-10
OK, I'm a long-time KDE-user who is only now properly trying out GNOME. And as you can guess, I have some minor issues.

In short: How do I really change icons in GNOME? I have checked the Theme-preferences, and it contains the "Theme Details" (IIRC), where one can change the icon-theme. And sure enough, when I change the theme, icons in Nautilus and desktop change like they should. But the toolbar-icons in Nautilus (for example) does not. How can I change the toolbar-icons as well?

---

### Post by Ramses de Norre on 2006-04-10
It depends on the icon theme you use, when a theme hasn't is own icons for some functions it refers to another theme (mostly gnome) to use those icons.
So it looks like they just remain then.
You can change the secondly used theme in ~/.icons/theme_name/index.theme, make/edit the line Inherits=theme_name with the theme name of the second theme.

---

### Post by Sushi on 2006-04-10
[QUOTE=Ramses de Norre]It depends on the icon theme you use, when a theme hasn't is own icons for some functions it refers to another theme (mostly gnome) to use those icons.
So it looks like they just remain then.
You can change the secondly used theme in ~/.icons/theme_name/index.theme, make/edit the line Inherits=theme_name with the theme name of the second theme.[/QUOTE]

Well, I wente through several icon-sets that were available on my system, and they all behaved in similar manner: icons in evolution and desktop (and taskbar) changed, toolbar-icons did not. IIRC, ONE icon in the toolbar changed (was it "Computer"?), but rest didn't change.

---

### Post by Ramses de Norre on 2006-04-10
Then they all don't have their own icons for it..

---

### Post by Sushi on 2006-04-10
[QUOTE=Ramses de Norre]Then they all don't have their own icons for it..[/QUOTE]

I would understand that if it happened with one or two icon-sets, bt since it happens with all icon-sets I have tried, I'm starting to feel that there's something wrong here.

---

### Post by Ramses de Norre on 2006-04-10
Try the attached icon theme, it should give you other icons in the nautilus toolbar.

---

### Post by Sushi on 2006-04-12
[QUOTE=Ramses de Norre]Try the attached icon theme, it should give you other icons in the nautilus toolbar.[/QUOTE]

Ah, much better :). Maybe the icons I tried were simply incomplete.

---

### Post by Ramses de Norre on 2006-04-12
A lot of themes don't have their own icons for everything. But by defining inherits you can combine a couple of themes to get an icon for everything.

---

### Post by jammodotnet on 2006-04-12
[QUOTE=Ramses de Norre]Try the attached icon theme, it should give you other icons in the nautilus toolbar.[/QUOTE]
@Ramses de Norre:
thank you for providing me with my first THEME/skin thingie.

I am a new 48 hours old user :)
still working on the dual-boot thing. but i feel i am almost there with the support from these forums.

---


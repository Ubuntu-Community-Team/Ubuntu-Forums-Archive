---
title: "Using KDE"
date: 2007-09-27
forum: Desktop Environments
---

### Post by PmDematagoda on 2007-09-27
Hello there, I want to start using KDE more as I've gotten used(But not bored) to the Gnome Desktop Environment, and I have some quesions about KDE:-

1)How do you change the theme of KDE, and how do you install themes?

2)How do you install desktop applets, such as CPU Temperature for Gnome?

3)Can you use Compiz-Fusion?

4)How do you organise your menu? Meaning how do you get rid of the unwanted icons, menu's and choices? And

5)How do you configure Keyboard Shortcuts?

I would really appreciate any feedback relating to any of these questions.:)

---

### Post by GeneralZod on 2007-09-27
> **PmDematagoda said:**
> Hello there, I want to start using KDE more as I've gotten used(But not bored) to the Gnome Desktop Environment, and I have some quesions about KDE:-

1)How do you change the theme of KDE, and how do you install themes?


Does System Settings have a Appearance and Themes -> Theme Manager panel? If not, install kcontrol, launch kcontrol, and go to Appearance and Themes -> Theme Manager -> Install New Theme.  Note that KDE themes will have the .kth extensions; KDE *styles* are executable code that, like all other executable code, will have to be compiled from source or, if a package exists in the repositories, installed via apt-get.

For whatever reason, KDE seems to have more styles available than themes, so a lot of people find it hard to "theme" KDE.  More on Themes vs Styles and why Kubuntu makes life even harder (I'm not sure if this is still the case, but it was once) [here](http://ubuntuforums.org/showthread.php?p=2304411#post2304411).

> 
2)How do you install desktop applets, such as CPU Temperature for Gnome?


You can't install GNOME desktop applets to my knowledge, but SuperKaramba has a wide selection of desktop widgets available via Get Hot New Stuff.

> 
3)Can you use Compiz-Fusion?


Yes, but I hear that KDE's pager in the panel may not be fully compatible with it.

> 
4)How do you organise your menu? Meaning how do you get rid of the unwanted icons, menu's and choices? And


Right-click on the K-Menu and select Menu Editor.

> 
5)How do you configure Keyboard Shortcuts?


Per-application ones can be altered via Settings->Configure Shortcuts; there's a search box to make it easier to find the actions you want.

"Global" shortcuts can be found in KControl->Regional And Accessibility->Keyboard Shortcuts, which allows you to set shortcuts for a wide range of actions (e.g. Switch to Next Desktop, etc).  To do arbitrary commands upon shortcut combos, use KControl->Regional and Accessibility->Input Actions.

Hope this helps! :)

---

### Post by PmDematagoda on 2007-09-27
Ok, I managed to change the theme, thank you GeneralZod.

But about the part of organising the Menu, it has the choice of deleting the Unwanted stuff. But if I do that, how do I get them back?

By the way can't you customise the colours of the styles such as the buttons, the menu, and the controls found at the top of a window?

---


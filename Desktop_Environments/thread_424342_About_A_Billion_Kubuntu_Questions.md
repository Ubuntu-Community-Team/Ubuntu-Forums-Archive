---
title: "About A Billion Kubuntu Questions"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Happy_Man on 2007-04-26
Hello everyone,

I've been a GNOME user from the start, but recently decided to acquaint myself with the other two DEs Canonical supports: Kubuntu and Xubuntu. So I ran sudo aptitude install kubuntu-desktop xubuntu-desktop, and started fiddling with them. After much fiddling, I have realized that I hate XFCE, and KDE is interesting, if not a refreshing change from GNOME. But that's not the point of this post. I have a few questions that my amazing amount of tweaking, settings-searching, and fiddling with sliders has not yet answered:

1. In Konqueror, is there any way to enable smooth scrolling, like in FIrefox?
2. Is there any unified Themes settings dialog, as in GNOME?
3. How do I change the text under icons on the desktop? (eg color, font, etc.)
4. What is Noatun?
5. Where do I change system sounds?
6. Where do I change mouse themes?
7. How do I change AmaroK themes?
8. If there isn't a unified Themes Settings dialog, how do I install all those themes off kde-look, as seen here:[http://www.kde-look.org/index.php?xcontentmode=8x9x10x11x12x13x14x15x16&PHPSESSID=2c915ab8643f423ed98e44c6c1ecc232](http://www.kde-look.org/index.php?xcontentmode=8x9x10x11x12x13x14x15x16&PHPSESSID=2c915ab8643f423ed98e44c6c1ecc232)
9. Is there a guide to using KDE effectively?

I'm really liking KDE so far, it seems very slick and polished. I like shiny. :lolflag: Anyway, thanks for any and all help given!

---

### Post by Nakkis on 2007-04-27
> **Happy_Man said:**
> Hello everyone,

I've been a GNOME user from the start, but recently decided to acquaint myself with the other two DEs Canonical supports: Kubuntu and Xubuntu. So I ran sudo aptitude install kubuntu-desktop xubuntu-desktop, and started fiddling with them. After much fiddling, I have realized that I hate XFCE, and KDE is interesting, if not a refreshing change from GNOME. But that's not the point of this post. I have a few questions that my amazing amount of tweaking, settings-searching, and fiddling with sliders has not yet answered:

1. In Konqueror, is there any way to enable smooth scrolling, like in FIrefox?
2. Is there any unified Themes settings dialog, as in GNOME?
3. How do I change the text under icons on the desktop? (eg color, font, etc.)
4. What is Noatun?
5. Where do I change system sounds?
6. Where do I change mouse themes?
7. How do I change AmaroK themes?
8. If there isn't a unified Themes Settings dialog, how do I install all those themes off kde-look, as seen here:[http://www.kde-look.org/index.php?xcontentmode=8x9x10x11x12x13x14x15x16&PHPSESSID=2c915ab8643f423ed98e44c6c1ecc232](http://www.kde-look.org/index.php?xcontentmode=8x9x10x11x12x13x14x15x16&PHPSESSID=2c915ab8643f423ed98e44c6c1ecc232)
9. Is there a guide to using KDE effectively?

I'm really liking KDE so far, it seems very slick and polished. I like shiny. :lolflag: Anyway, thanks for any and all help given!
1. Smooth scrolling is built into KDE styles themselves, although not all styles support it. Check out Domino from kde-look.org, it supports smooth scrolling. 
2. Yes there is, but for some reason Ubuntu ships with a "dumbed down" version of KDE control panel. Run 'kcontrol' to use the full KDE control center. Check out Appearance & Themes -> Theme Manager
3. You can change the font in KDE Menu -> System Settings -> Appearance -> Fonts -> Desktop font
4. Noatun is some kind of a audio player, that I usually uninstall as soon I install Kubuntu. Never tried it. :) 
5. You can change them in 'System notifications' in the control center.
6. Atleast in the "real" control center (kcontrol) you can change it at Peripherals -> Mouse -> Cursor Theme. I don't know about the Ubuntu version of kcontrol where you can change it but it should be the same place where you configure your mouse. :( 
7. If you mean the context sidebar themes, you can download more themes in Settings -> Configure Amarok -> Appearance -> Download styles. Other widgets are controlled by the KDE styles and colours. 
8. That link leads to the home page of kde-look.org but if you mean the theme manager themes see answer #2. 
9. Check out [KDE User Guide](http://docs.kde.org/development/en/kdebase/userguide/index.html). I had a good PDF guide for KDE somewhere...I'll let you know if I find it.

---

### Post by Happy_Man on 2007-04-27
How do I install Domino? And another thing; in Konqueror, whenever I open it up, it loads the text at a very small font. I have to zoom in to make it readable. Any way to fix that?

---

### Post by disturbedite on 2007-04-27
umm, i've never looked before and found it in two seconds.  go to settings, appearance, and font size is right there.

btw, where'd you get that avatar Happy_Man?  i'd like to use it for my firefox icon but i'd like a little bit bigger version if there is one.  (svg would be nice).

---

### Post by Happy_Man on 2007-04-27
Oh.... I feel stupid. The avatar is off of Gnome-Look. [http://gnome-look.org/content/show.php/Firefox+Icons?content=47617](http://gnome-look.org/content/show.php/Firefox+Icons?content=47617)

---

### Post by disturbedite on 2007-04-27
sorry if my post made you feel stupid, i didn't intend it to.  thanks for that link too!

---

### Post by Happy_Man on 2007-04-27
Incidentally, when poking around the System Settings, I see an option for effects. If I try to enable them, they don't work. Is there a fix for that?

---

### Post by Nakkis on 2007-04-28
> **Happy_Man said:**
> How do I install Domino? And another thing; in Konqueror, whenever I open it up, it loads the text at a very small font. I have to zoom in to make it readable. Any way to fix that?
Install 'kde-style-domino' from the Ubuntu repositories to install Domino (atleast Feisty repos have it now). You can edit the font size in Konqueror preferences. To use the KDE GUI effects you need a video card and drivers that support the 'Composite' extension of X.org. Which card do you have?

---

### Post by hellblade on 2007-04-28
I don't think it exists in the official repos. You can still get the edgy version from [http://www.kde-look.org/content/show.php/Domino+Kubuntu+package?content=52864](http://www.kde-look.org/content/show.php/Domino+Kubuntu+package?content=52864) which wotks in feisty too.

---

### Post by Nakkis on 2007-04-28
> **hellblade said:**
> I don't think it exists in the official repos. You can still get the edgy version from [http://www.kde-look.org/content/show.php/Domino+Kubuntu+package?content=52864](http://www.kde-look.org/content/show.php/Domino+Kubuntu+package?content=52864) which wotks in feisty too.
You're correct. It was my own chekinstall-install that I saw when I searched for domino.

---

### Post by Happy_Man on 2007-04-28
Well,  my card is a nvidia geforce mx 420, but as it can run Beryl and stock Compiz just fine, I don't think there should be a problem with that...

And do you have to compile themes?

---

### Post by Jucato on 2007-04-29
> **Happy_Man said:**
> Hello everyone,

I've been a GNOME user from the start, but recently decided to acquaint myself with the other two DEs Canonical supports: Kubuntu and Xubuntu. So I ran sudo aptitude install kubuntu-desktop xubuntu-desktop, and started fiddling with them. After much fiddling, I have realized that I hate XFCE, and KDE is interesting, if not a refreshing change from GNOME. But that's not the point of this post. I have a few questions that my amazing amount of tweaking, settings-searching, and fiddling with sliders has not yet answered:

1. In Konqueror, is there any way to enable smooth scrolling, like in FIrefox?
2. Is there any unified Themes settings dialog, as in GNOME?
3. How do I change the text under icons on the desktop? (eg color, font, etc.)
4. What is Noatun?
5. Where do I change system sounds?
6. Where do I change mouse themes?
7. How do I change AmaroK themes?
8. If there isn't a unified Themes Settings dialog, how do I install all those themes off kde-look, as seen here:[http://www.kde-look.org/index.php?xcontentmode=8x9x10x11x12x13x14x15x16&PHPSESSID=2c915ab8643f423ed98e44c6c1ecc232](http://www.kde-look.org/index.php?xcontentmode=8x9x10x11x12x13x14x15x16&PHPSESSID=2c915ab8643f423ed98e44c6c1ecc232)
9. Is there a guide to using KDE effectively?

I'm really liking KDE so far, it seems very slick and polished. I like shiny. :lolflag: Anyway, thanks for any and all help given!

1. This is not dependent on your widget style or theme. In Konqueror, go to the Settings menu, Configure Konqueror, Web Behavior options. Uncheck the Middle click opens URL in selection option.

2. Don't be deceived by the Theme Manager in KDE. It is not that power really. If you want to learn why, read [https://help.ubuntu.com/community/CustomizeKubuntu](https://help.ubuntu.com/community/CustomizeKubuntu)

3. As for the font color of text on the Desktop, right-click on the desktop, Configure Desktop, Appearance options, then click on the Advanced Settings. There is a setting there for the font color.

4.Noatun si the official audio player of the KDE 3 release, if I remember correctly. Not installed by default on most KDE distributions anyway. Go Amarok!!

5. KControl -> Sound & Multimedia -> System Notifications... or System Settings -> Notifications -> System Notifications

6. ... or System Settings -> Keyboard and Mouse -> Mouse. Note, you need to restart the X server for changes to take effect.

7. answered already
8. Link is probably wrong

9. The KDE User Guide in KHelpCenter (K Menu -> Help) is a good one. PDF version is available here: [http://docs.kde.org/](http://docs.kde.org/) (upper right box).

---


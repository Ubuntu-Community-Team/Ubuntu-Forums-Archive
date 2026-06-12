---
title: "How to change panel background?"
date: 2010-01-19
forum: Desktop Environments
---

### Post by Koraq on 2010-01-19
I just upgraded and now my panel looks odd. I guess it's the new std colour scheme or theme, but my panel looks grey with some fairly ugly stripes of lighter gray. It's kind of hard to see the buttons on the panel when it's not of a uniform colour. 

How do I change the appearance of my panel? I have tried to change colour sets, but it only affected windows. 

Suggestions? I guess the setting is in there somewhere...

My version:
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

and 
$ dpkg-query -l | grep kdebase
ii  kdebase                                    4:4.3.4-0ubuntu1~karmic1                   base applications from the official KDE release
ii  kdebase-bin                                4:4.3.4-0ubuntu1~karmic1                   core binaries for the KDE 4 base module
ii  kdebase-data                               4:4.3.4-0ubuntu1~karmic1                   shared data files for the KDE 4 base module
ii  kdebase-plasma                             4:4.3.4-0ubuntu1~karmic1                   Transitional package for plasma-widget-folderview.

---

### Post by Zorael on 2010-01-19
The grey panel with the stripes is the opaque (non-transparent) panel of the **Air** plasma theme, default in 4.3 and 4.4. It is usually only visible if you have compositing disabled. Enabling that should remove the stripes and make it transparent, causing it to assume a tint of the wallpaper color behind it.

So your options are to either enable compositing (if your hardware allows and you even want to), or to change the panel theme. You can do the latter in System Settings -> Advanced tab -> Desktop Theme details. If I remember the behavior correctly, as soon as you modify a theme it will create a (Customized) theme with which you can toy around with.

At least in 4.4, you ultimately pick what theme to use in System Settings -> Appearance -> Style -> Workspace tab. I believe it used to be in the Desktop Activity settings window you can reach by right-clicking your desktop workspace. It's the same screen where you change your wallpaper. It may default to (Customized), not sure.

I use the Air theme with an Aya panel. I believe it tries to match your theme coloring so it's always a good match. It also stays fairly opaque even with compositing enabled, when it normally turns transparent.

---

### Post by Koraq on 2010-01-19
I prefer to disable compositing, which I find is a Apple invented junk which look pretty without usefulness.

That it's possible to change the appearance some other way makes me happy! Choice is good.

The only snafu was that nothing happened when I tried to enable my modified theme, until I right clicked on the desktop and through the settings alternative there installed a new theme and then picked something else (!), like my newly created one.

Thanks a bunch! Problem solved.

---


---
title: "Gnome themes not installed properly!"
date: 2009-07-23
forum: Desktop Environments
---

### Post by vickoxy on 2009-07-23
:confused: So, i downloaded several themes from here - *[http://www.gnome-look.org/](http://www.gnome-look.org/)* - (GTK 2.x, tried also Compiz, Emerald...), but only 1 or 2 themes was i able to install properly (right click-change desktop, install...) Other themes i was not able to  install-or it says that theme is installed, but i have no new themes, only few new frames or colors schemes). What do i do wrong? BTW which themes should i install on my Dell Mini 9 running jaunty 9.04?

Thanks

---

### Post by mcduck on 2009-07-23
First thing you should know is that most themes actually don't contain themes for everything, just a single part (GTK theme, window border theme for some window manager, or icons. Not all of them)..

Available "full " theme sets can probably be counted on the fingers of one hand.

After that, if you find a theme that can't be installed by dropping the package to the themes window the archive you downloaded most likely contains several themes, each in their own archives inside the one you downloaded. In that case extract the first archive and then try again installing the contained theme archives.

And in the end, if everything else fails, just extract the theme yourself. Put GTK and Metacity themes into ~/.themes and icon themes into ~/.icons.

---

### Post by vickoxy on 2009-07-23
> **mcduck said:**
> First thing you should know is that most themes actually don't contain themes for everything, just a single part (GTK theme, window border theme for some window manager, or icons. Not all of them)..

Available "full " theme sets can probably be counted on the fingers of one hand.

After that, if you find a theme that can't be installed by dropping the package to the themes window the archive you downloaded most likely contains several themes, each in their own archives inside the one you downloaded. In that case extract the first archive and then try again installing the contained theme archives.

And in the end, if everything else fails, just extract the theme yourself. Put GTK and Metacity themes into ~/.themes and icon themes into ~/.icons.


Thanks for answer-well i am newbie so i didn´t know that-but i supposed that something like that should be, because, everything works just fine...

It is true-only few themes are "full". :popcorn:

---


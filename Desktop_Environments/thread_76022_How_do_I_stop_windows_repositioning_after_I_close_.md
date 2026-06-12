---
title: "How do I stop windows repositioning after I close them?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by kayas80 on 2005-10-14
Whenever I reposition or resize any window - be it either Nautilus, Amarok, Firefox or any other - it moves back it it's original position after it's been closed and re-opened. Is there anyway to stop this from happening? It's really annoying me!

Thanks

---

### Post by Wolki on 2005-10-14
[QUOTE=kayas80]Whenever I reposition or resize any window - be it either Nautilus, Amarok, Firefox or any other - it moves back it it's original position after it's been closed and re-opened. Is there anyway to stop this from happening? It's really annoying me![/QUOTE]

Nautilus will remember size and position when you disable the browser mode. Spatial nautilus, you either love it or hate it... :)

You can set window positions and sizes with devilspie, but it's configuration can be a little bit intimidating (and you will have to rewrite the config to change to new default positions/sizes), but it is very very powerful.

Here's a link to my (detailed) howto: [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

---

### Post by kayas80 on 2005-10-14
[quote=Wolki]Nautilus will remember size and position when you disable the browser mode. Spatial nautilus, you either love it or hate it... :)

You can set window positions and sizes with devilspie, but it's configuration can be a little bit intimidating (and you will have to rewrite the config to change to new default positions/sizes), but it is very very powerful.

Here's a link to my (detailed) howto: [http://ubuntuforums.org/showthread.php?t=75749]("http://ubuntuforums.org/showthread.php?t=75749")[/quote]

That's a great how to but it's a bit more than i'm, perhaps, capable of

---

### Post by Wolki on 2005-10-14
[QUOTE=kayas80]That's a great how to but it's a bit more than i'm, perhaps, capable of[/QUOTE]

It's not as difficult as it looks, I tried to anticipate all the errors that could happen from the start ^^;;;

I can try to create a sample file for you if you want.

[edit] wow, I managed to say the exact opposit of what i meant to say... I need sleep. -_-;

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=kayas80]Whenever I reposition or resize any window - be it either Nautilus, Amarok, Firefox or any other - it moves back it it's original position after it's been closed and re-opened. Is there anyway to stop this from happening? It's really annoying me![/QUOTE]

I'm pretty sure that's just how most window managers work, especially GNOME's standard window manager, Metacity. All window managers have what's called a "placement model". Some will begin by placing windows in the top left corner and cascading them downwards and to the right. Others will place a new window under your pointer. TWM (a very primitive window manager) will make you manually place new windows with a mouse click. As I remember, Enlightenment had multiple placement models, and also had a "Remember" dialog that let you save various aspects of a window's state, like its position.

Also, most X apps have a --geometry switch, which you could use if you were making a menu by hand to set a window's position and size to suit your preferences.

---


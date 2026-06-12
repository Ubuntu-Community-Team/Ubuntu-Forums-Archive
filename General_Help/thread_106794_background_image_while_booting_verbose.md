---
title: "background image while booting verbose"
date: 2005-12-21
forum: General Help
---

### Post by ssalman on 2005-12-21
I’ve recently switched off my usplash by removing the [COLOR=Blue]"splash" [/COLOR]option from GRUB’s [COLOR=Blue]menu.lst[/COLOR] file, and by adding [COLOR=Blue]“vga=0x317”[/COLOR] I now have Ubuntu boot the way I like it, except for one thing… before using Ubuntu I was using Suse 9.3, and there was an option to do a verbose boot that will have a default image in the background as boot messages print on top. I was wondering if there is a way to do this in Ubuntu? Is this a usplash functionality? And can I configure usplash?

One last question ;) ... Do I need to uninstall usplash, or disabling is just fine?

---

### Post by gnu2tux on 2005-12-21
As far as I believe, Ubuntu doesn't have the tux xpm file as a bootloader background. It is possible to add yourself, but you'll have to google around a bit for the answer as I have tried, and failed before!

With regards to usplash, leaving it installed will be fine.

Cheers,

---

### Post by c_dog on 2005-12-21
The SuSE bootsplash does this by running it's own special mini X server that has   mulitple consoles that do the bootloader duties and pull up the Display Manager. AFAIK Upslash doesn't quite take over control of things so much on it's own.

---

### Post by LuisC-SM on 2006-01-04
[QUOTE=c_dog]The SuSE bootsplash does this by running it's own special mini X server that has   mulitple consoles that do the bootloader duties and pull up the Display Manager. AFAIK Upslash doesn't quite take over control of things so much on it's own.[/QUOTE]

Take a look to this thread
[http://www.ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash+image](http://www.ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash+image)

Hope it helps

---

### Post by ssalman on 2006-01-12
Thanks LuisC-SM, but my question is for a splash BG while booting Ubuntu after Grub is done.__

---


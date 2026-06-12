---
title: "Speeding up Desmume"
date: 2013-07-18
forum: Emulators
---

### Post by Transmutable on 2013-07-18
Is there any way to speed up Desmume? I was getting ~25fps with gtk, by switching to gtk-glade, turning off sound, and putting frameskip to 9 I'm still only averaging 40fps. It's almost unplayable. I can't seem to find any controls or preferences to change, like are suggested in speeding it up in Windows. I'm playing Pokemon Black 2, which I own, I just can't find my DS.

Is no$gba any faster? I'd rather not install WINE if I can help it, but if it plays at a normal speed I'd do it.

---

### Post by jeremyw2 on 2013-08-20
Desmume is a very demanding emulator, sometimes the only way to achieve better performance is by getting a faster CPU. BUT if you want to try disabling all render filters (Top of screen menu >> Config >> Primary Interpolation >> Set to None) it might squeeze a couple of extra FPS from it. I have an AMD FX-8320@4.4GHz and it still has trouble maintaining 60FPS in New Super Mario Bros. Newer Intel i3-i5-i7 CPUs will fare better, though, as they have better single core performance. Desmume doesn't seem to be heavily multithreaded as it only maxes out one of my CPU cores.

Also you stated you "[COLOR=#000000]can't seem to find any controls or preferences to change"[/COLOR] try having a look at the top of the screen, there should be a typical applications menu there. I couldn't find the Config menu for the longest time.

---


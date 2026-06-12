---
title: "KDE menu too big?"
date: 2009-10-16
forum: Desktop Environments
---

### Post by PHaLaNX on 2009-10-16
KDE kept forgetting about my resolution settings so i figured installing ATI drivers could fix it, but now after installing the drivers everything seems too big. 

Like in here: 

[IMG]http://img251.imageshack.us/img251/3148/snapshot1r.gif[/IMG]

The menu takes all the screen, it didn't used to be like this. 

Any idea how to fix it? Also how can I make my resolution setting permanent?

---

### Post by WinterMadness on 2009-10-16
I dont see any image or link

but you can resize the kick off menu just like any window.

click the K and when it loads up, just goto the top right corner and resize.

---

### Post by Ubuntiac on 2009-10-17
Eep! Unless I'm mistaken... I think that's KDE 3.5! I haven't seen that since May '07...

One way to fix it would be to download the new version (Karmic comes out on the 30'th) and install that. Despite old thread posts about KDE 4.0, the current KDE is far more configurable imho than 3.5. Part of that includes the menu size. :)

Beyond that, I don't remember any way of resizing the menu in KDE 3.5. Sounds more like a screen res thing though. This is likely fixable by setting screen resolution to what you want in xorg.conf (Google it).

Good luck!

---

### Post by PHaLaNX on 2009-10-17
Yas, it's KDE 3.5.10. It was fine when I installed but then every font or menu just got out of proportion. I guess I'll give KDE 4 another shot because of these problems.

Thanks.

---

### Post by theZoid on 2009-10-17
> **PHaLaNX said:**
> Yas, it's KDE 3.5.10. It was fine when I installed but then every font or menu just got out of proportion. I guess I'll give KDE 4 another shot because of these problems.

Thanks.

Did you go into Control Center and force your dpi to 96?  If you don't, that's usually what you're gonna get :)

---

### Post by PHaLaNX on 2009-10-17
I'd tried that, it did nothing though. 

I solved the problem by adding 

```

Virtual   1024 768
```

into the xorg.conf file like this:

```
Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1024 768
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Even though the resolution was 1024x768 adding this line made the trick. 

Thanks to all who have answered.

---


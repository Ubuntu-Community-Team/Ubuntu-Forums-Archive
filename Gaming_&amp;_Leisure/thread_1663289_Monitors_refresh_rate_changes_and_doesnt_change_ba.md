---
title: "Monitors refresh rate changes and doesnt change back"
date: 2011-01-09
forum: Gaming &amp; Leisure
---

### Post by sakuramboo on 2011-01-09
I have been trying to wrap my head around this little problem, but maybe I'm just over thinking this. Here is what happens.

Certain games, when run full screen, will change the monitors refresh rate to 60hz. This would normally be okay, but I run my monitor at 75hz. 60hz will produce a fuzzy look, making everything look blurry. When I exit the game, the desktop does not change back to 75hz.

I have noticed that some games allow me to specify what refresh rate to use, but many do not. It is to my understanding that OpenGL will default to the first available refresh rate, which would be 60hz, completely disregarding the settings I currently use.

I was thinking that for a quick work around, I would edit the xorg.conf, create a subsection and only specify a 1280x1024_75 mode, or, copy the modeline from nvidia's settings. I haven't tried this yet because I wanted to keep xorg.conf edits as a last resort.

Does anyone else have any insight on this?

---


---
title: "Played with display settings and now I can't see screen in Gnome"
date: 2009-04-17
forum: General Help
---

### Post by poit on 2009-04-17
I did something stupid. It's on Jaunty using Gnome on an old ATI graphics card. (Thinkpad T30)

I started playing with the display settings and clicked on the rotate display option. The display immediately went blank. Now when I boot up, once I log on I have no display. I've tried the Xorg rebuild option on boot but id doesn't help. I'm sure there is some file I can edit in text mode to fix this, I just don't know where to look. HELP!

Thanks

---

### Post by danwood76 on 2009-04-17
YOu can delete the screen settings quite easily.

login into a termnial, either by doing a failsafe-gnome terminal or a tty.
then run this:
```

rm ~/.config/monitors.xml

```
This will reset all your monitor settings, I did the same thing once... ;)

---

### Post by poit on 2009-04-17
Thanks, that did it! Hours of searching, 10 seconds to fix it.

---


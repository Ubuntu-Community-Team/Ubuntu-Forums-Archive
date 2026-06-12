---
title: "windows icons and fonts"
date: 2009-06-29
forum: Desktop Environments
---

### Post by johnh10000 on 2009-06-29
Well thats it really how can I use windows ttf under ubuntu, if possible,
Also how do I use windows icons, under gnome?

A daft one I know but here goes, any chance I could use a windows screensaver under ubuntu?  I do have wine installed if that helps.

Not optimistic on the last one.

cheers

---

### Post by kerry_s on 2009-06-29
**sudo apt-get install ttf-mscorefonts-installer**

will install the windows fonts.

icons, you need to find a theme pack thats compatible.

screen saver, no
you might be able to find something similar.

---

### Post by johnh10000 on 2009-06-29
> **kerry_s said:**
> **sudo apt-get install ttf-mscorefonts-installer**

will install the windows fonts.

icons, you need to find a theme pack thats compatible.

screen saver, no
you might be able to find something similar.

I doubt it, it's the bbc ashes to ashes ones.  oh well.

I guess I could manually convert the icons

And I'm going to install that now

---

### Post by mcduck on 2009-06-29
> **johnh10000 said:**
> Well thats it really how can I use windows ttf under ubuntu, if possible,
Also how do I use windows icons, under gnome?

A daft one I know but here goes, any chance I could use a windows screensaver under ubuntu?  I do have wine installed if that helps.

Not optimistic on the last one.

cheers

Ubuntu fully supports TTF fonts, so if you want more than what's included in msttcorefonts package you can simply manually copy your fonts from Windows. Put them in to /usr/share/fonts to install them system-wide, or ~/.fonts for your user only.

Icons, like already said, would have to be renamed, and repackaged to turn them into a icon theme that works in Linux. I've seen some people using a theme like this, so it probably already exists and you'll just to find it.

Screensavers are a strict no. They are programs, and programs made for one operating system don't run in others. I really doubt Gnome-screensaver or Xscreensaver would allow running anything through Wine, and in the end your Windows screensavers most likely rely on DirectX anyway.

---


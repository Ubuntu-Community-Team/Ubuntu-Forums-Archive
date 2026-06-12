---
title: "resolution not satisfactory"
date: 2010-02-22
forum: Desktop Environments
---

### Post by skawars on 2010-02-22
Having dual booted with Windows 7, and now using Ubuntu almost 100% of the time, there's just one thing that bugs me..

All of my programs look a little but too big compared to how they used to in windows.

I've checked the display preferences and it's at the maximum (1366 x 768), and the text i'm writing now looks correct size, it's just all my windows look oversized in comparison.

For example at the top of firefox, the address bar, a bookmarks bar, google toolbar and a few tabs takes up almost a 3rd of the screen, and everything could do with just downsizing a little, any ideas?

---

### Post by mcduck on 2010-02-22
go to gnome-look org, find a compact GTK theme, and install that.

If the resolution is correct and the txt size is correct there's nothing else left to change than the theme itself.

---

### Post by skawars on 2010-02-22
Okay thanks I'll give it a try later. Dunno if it's just because I'd adjusted to pretty small sized windows in w7, it just looked ridiculously oversized, as if i'd switched from 1024 x whatever to 800 x whatever. And I switched DOWN to 1024 out of curiousity and it looked like 640 x 480 or something!

anyway i'll have a try with a compact theme, cheers

---

### Post by mcduck on 2010-02-22
oh, I just remembered, I *do* know some tricks that allow you to gain a bit of extra room:

1. Go to System/Preferences/Appearance, Interface-tab, and make sure "Toolbar Button Labels" is set to "Icons only" or "Text beside items". (I think this is already the default in latest Ubuntu versions)

2. Press Alt-F2 and run gconf-editor. Use that to browse to desktop/gnome/interface, find the "toolbar_icons_style"-key and change it's value to "small-toolbar". 

3. Once again, System/Preferences/Appearance, Fonts-tab, click the Details-button and set the resolution DPI value to the correct value for your display size & resolution. Actually that should be done anyway if you want your fonts to render correctly.

4. many applications, like Firefox, OpenOffice, Inkscape and Gimp, also have their own settings for icon sizes.. You should definitely check their options if you are low on screen space. 

..but after all those it really is the GTK theme and your font size that define how much space all the user interface items take. Of course you might want to find some slim theme for your window borders as well.

---


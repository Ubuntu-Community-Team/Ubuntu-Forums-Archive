---
title: "control of the window background colors doesn't work"
date: 2010-01-06
forum: Desktop Environments
---

### Post by sidewalkcynic on 2010-01-06
How can I control the window background colors of a file browser?

Gnome promises:
Edit> Backgrounds and Emblems

but, it doesn't work - I drag a swatch to the window background, and it doesn't work. this would be an excellent feature to exploit, but it doesn't work.

---

### Post by ajgreeny on 2010-01-06
Have you looked in System->Preferences->Appearance->Theme tab, where you can change this, or are supposed to be able to (I've never tried) in the Customise->Colours.

---

### Post by mcduck on 2010-01-06
> **sidewalkcynic said:**
> How can I control the window background colors of a file browser?

Gnome promises:
Edit> Backgrounds and Emblems

but, it doesn't work - I drag a swatch to the window background, and it doesn't work. this would be an excellent feature to exploit, but it doesn't work.
Works fine for me. All I do is drag&drop the color/pattern I want to the Nautilus window. Where *exactly* are you trying to drop the color?

Note that emblems are applied to icons, while colors & patterns apply to the window background.

Also the only way to get different backgrounds in different directories is to set the background while Nautilus is in spatial mode. Setting the background in browser mode sets the default background for *all* directories (except for the ones that have a background already set in spatial mode).

> **ajgreeny said:**
> Have you looked in System->Preferences->Appearance->Theme tab, where you can change this, or are supposed to be able to (I've never tried) in the Customise->Colours.
I doubt that he means GTK background color, at least the post doesn't give any reason to assume so.

---

### Post by sidewalkcynic on 2010-01-06
> **mcduck said:**
> Works fine for me. All I do is drag&drop the color/pattern I want to the Nautilus window. Where *exactly* are you trying to drop the color?

Note that emblems are applied to icons, while colors & patterns apply to the window background.

Also the only way to get different backgrounds in different directories is to set the background while Nautilus is in spatial mode. Setting the background in browser mode sets the default background for *all* directories (except for the ones that have a background already set in spatial mode).maybe that's my problem - let me check it out...

... yeah, that's it.

So, why can't it work for list view, and I thought I would be able to make different folders different colors???

---

### Post by mcduck on 2010-01-07
In theory it could work for the list view, the problem is that there's usually no empty background visible anywhere.. So there really is no place where to drop the color/pattern.

And yes, you can make the directories use different colors. But not the icons, just the background you see when browsing inside that directory. For icons you have to either change the icon itself, or just use the emblems. Making the icon color changeable while still maintaining the themeability would be quite hard (either all icons would have to be SVG images, or themers would have to make every icon in multiple colors which would be quite a lot to ask considering that making an icon theme is already a lot of work to do..)

---


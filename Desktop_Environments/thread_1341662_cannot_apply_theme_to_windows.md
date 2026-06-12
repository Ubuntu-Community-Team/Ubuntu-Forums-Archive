---
title: "cannot apply theme to windows"
date: 2009-11-30
forum: Desktop Environments
---

### Post by iRounak on 2009-11-30
I downloaded the theme: 
[http://www.compiz-themes.org/content/show.php/Black+Crystal+y?content=101121](http://www.compiz-themes.org/content/show.php/Black+Crystal+y?content=101121)

If I 
1. open Emeral Theme Manager 
2. select the theme mentioned above
3. go to "Edit Themes"
4. go to "Theme"
then i see transparent windows in the "Screenshot".
However when I apply the theme with "emerald --replace" only the window title bar is transparent. The window does not become transparent.
Please help.

---

### Post by lidex on 2009-11-30
Emerald is a window decorator, which means it affects window borders, controls, etc. Compiz/Metacity are window managers and control such things as window opacity.

---

### Post by iRounak on 2009-11-30
Compiz is over-whelming. Can you tell me what exactly I should change in Compiz

---

### Post by lidex on 2009-11-30
You can get started here:
[http://forlong.blogage.de/en/entries/2007/8/29/How-to-set-up-Compiz-Fusion#comments]("http://forlong.blogage.de/en/entries/2007/8/29/How-to-set-up-Compiz-Fusion#comments")
More here:
[http://wiki.compiz.org/]("http://wiki.compiz.org/")

*BTW that transparency you saw in that screenie was a termimal window which supports it's own via preferences.*

---

### Post by iRounak on 2009-11-30
I found something here: [http://wiki.compiz.org/GeneralOptions#Opacity_Settings](http://wiki.compiz.org/GeneralOptions#Opacity_Settings)

But I dont have "Opacity Settings" in General options.

---

### Post by lidex on 2009-11-30
Try "Opacity, Brightness, and Saturation" in Accessibility section.

---

### Post by iRounak on 2009-11-30
Thanks again. The shortcuts that I set for increasing and decreasing transparency in  "Opacity, Brightness, and Saturation" work. But I don't know how to make windows transparent by default.

---

### Post by lidex on 2009-11-30
> But I don't know how to make windows transparent by default. 
AFAIK that can't be done. :frown:

---

### Post by stinkeye on 2009-11-30
> **iRounak said:**
> Thanks again. The shortcuts that I set for increasing and decreasing transparency in  "Opacity, Brightness, and Saturation" work. But I don't know how to make windows transparent by default.

[COLOR="Red"]***WARNING-MOVE YOUR "WINDOWS VALUE"  SETTING UP BEFORE PASTING IN***
[/COLOR]or you wont see any windows.
[ATTACH]138138[/ATTACH]
In Opacity, Brightness, and Saturation add a new window specific feature
```
(type=Normal | Dialog | ModalDialog | Unknown)
```

Having all your windows transparent gets pretty annoying after a while.
I like to have just menus and popups transparent```
 Menu | PopupMenu | DropdownMenu
```
or just choose which windows you want transparent by clicking on the + button in the
first window that comes up and then the grab button.Click on the window you want transparent.

---

### Post by iRounak on 2009-11-30
Many thanks stinkeye.
> I like to have just menus and popups transparent
I have to agree with you and I would add Terminal to that list. Transparency is attractive but it has its own issues especially for someone like me who reads a lot of text. Currently, I have been able to put together a Mac OS like serene theme:
[http://img413.imageshack.us/img413/2157/screenshot1uw.png](http://img413.imageshack.us/img413/2157/screenshot1uw.png)

---

### Post by stinkeye on 2009-11-30
Looks like a nice easy on the eye theme.
This is what I'm currently using

---

### Post by iRounak on 2009-11-30
cool :)

---


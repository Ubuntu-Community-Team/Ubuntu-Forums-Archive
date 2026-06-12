---
title: "Change font color in OpenOffice toolbar"
date: 2007-06-06
forum: Desktop Environments
---

### Post by ashrack on 2007-06-06
On all of the GTK2 apps the default font color is white in the UPPER TOOLBAR where file, edit, insert, format, etc are. Except in OpenOffice the color is black. Which makes it kinda hard to read when I am using this theme.
See the screenie for a more visual description and look in the upper toolbar.
[ATTACH]34515[/ATTACH]

Is there a way to change the font color to white?

---

### Post by ashrack on 2007-06-07
bump

---

### Post by steeleyuk on 2007-06-07
Tools > Options > Appearance tab

Edit: sorry thats for the document. I'll keep digging, i'm sure theres an option for it...

---

### Post by ashrack on 2007-06-07
I already tried that option only to find it that it only changes the color of fonts in documents.

Tnx4 trying

---

### Post by FuturePilot on 2007-06-07
I also have this problem with a theme. Only it's worse because the toolbar is black and so are the fonts. Almost impossible to read. Same thing happens with Firefox.
[http://ubuntuforums.org/showthread.php?t=453073]("http://ubuntuforums.org/showthread.php?t=453073")

Is there a way to fix this?

---

### Post by ashrack on 2007-06-07
I have already asked over at OOO forums and they said I should try the official OOO. 
And I also asked this question to UBUNTU's mailling list and haven't received a reply yet. 
Perhaps we should open a bug report on LP?

---

### Post by FuturePilot on 2007-06-07
We could always try and see what happens. It seems that the problem is that the Firefox and Open Office toolbar text is black and cannot be changed.

---

### Post by GraveyardPC on 2007-06-13
I've been having the same OpenOffice menu issue, as well. It has to do with OO not being a real GTK program, it's actually Java based. Firefox however is GTK based, and the black menu text can be altered in the "userChrome.css" file found in your "~/.mozilla/firefox/*.default/chrome" directory. Append it with the following lines (if the file doesn't exist -- create it):

```
#file-menu, #edit-menu, #view-menu, #go-menu, #history-menu,
#bookmarks-menu, #tools-menu, #helpMenu{
color: #ffffff !important;}
```

---

### Post by bluemech on 2007-07-01
Bumping back. Has anyone found the fix for OpenOffice yet?

---

### Post by xl_cheese on 2007-07-30
the fix:

class "GtkMenuItem"					style "theme-menu-item-black" 
class "GtkTearoffMenuItem"				style "theme-menu-item-black" 
class "GtkImageMenuItem"				style "theme-menu-item-black" 
widget_class "*MenuItem.*"				style "theme-menu-item-black" 

inside the style I have called "theme-menu-item-black"  I added the following to change the OOO menu font color:

  text[NORMAL]	= "#000000"  # for black font.  "#FFFFFF" for white font.

---

### Post by ashrack on 2007-07-31
where do I input this code?

---

### Post by Hagar Delest on 2007-08-01
In the *gtkrc* file of the theme you use. Located in ~/.theme/theme_used/gtk2/.

But it works only if the menus are also with dark background IIRC. This is a real problem when the theme has dark titlebar and white menus (like LINSTA).

---

### Post by LuisC-SM on 2007-12-06
> **xl_cheese said:**
> the fix:

class "GtkMenuItem"					style "theme-menu-item-black" 
class "GtkTearoffMenuItem"				style "theme-menu-item-black" 
class "GtkImageMenuItem"				style "theme-menu-item-black" 
widget_class "*MenuItem.*"				style "theme-menu-item-black" 

inside the style I have called "theme-menu-item-black"  I added the following to change the OOO menu font color:

  text[NORMAL]	= "#000000"  # for black font.  "#FFFFFF" for white font.

Hi.

This is good too know,
I've been using a theme named  Moomex and it has a nice green-blue menu bar, I think it is a lot better than LinstaIs NotVista,

I've seen your next post but I still do not have a clue on whrere I should insert those values., specially the last one

Could it be possible  that you show us your gtkrc file?

Thanks in advance

Luis

---


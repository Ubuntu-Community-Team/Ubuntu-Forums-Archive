---
title: "Changing menu bar icon"
date: 2006-06-29
forum: Desktop Environments
---

### Post by juanlu on 2006-06-29
Hello all,

I've tried to change ubuntu icon on the menu bar in gconf but it doesn't work, i also tried it replacing distributor-logo but i have same result.

I've been looking in the forum but i don't see another solution.

I'm using dapper, and i find other people asking the same. Is there some problem in dapper with this?

thank you

---

### Post by Jucato on 2006-06-29
which size of the distributor-logo icon were you trying to replace? replace the 48x48 icon from the hicolor icon set (/usr/share/icons/hicolor/ if I'm not mistaken), then remove the Main Menu/Menu Bar from the panel, and put it back again (so that the icon will be refreshed).

That's what I did in Dapper.

EDIT: Remember to keep a copy of the original distributor-logo, just in case you want to put it back again.

---

### Post by juanlu on 2006-06-30
Thank you, but it not works.

It was 48x48 icon what I replaced. I revised other formats (16x16, 92x92, ...) and there is no distributor-logo in it.

Perhaps the menu-bar is taken another icon in another location?

 I think that modifying custom icon option in gconfig will not work at all, because it only applies if the object is menu-object or drawer-object. If the object is menu-bar this option doesn't apply.

Excuse my bad english, it is not my native language,

thanks

---

### Post by Mr. Picklesworth on 2006-08-17
I am trying to do something like this as well, but to actually remove the icon altogether.
Instead, I want that nice little icon to be a seperate clickable item, opening the Ubuntu System Panel.

---

### Post by 1oki on 2006-08-31
I followed what Fenyx said... and I was able to change the icon for the menu, but not the menu bar! when I go to remove it from the bar after being changed and add it using the "add to pannel feture", it shows the menu bar as being the icon that I set, but when i add it it doesnt work...still ubuntu. Is there a way to change this one? not just the menu, but the menu bar!?

---

### Post by arkangel on 2006-08-31
@juanlu

remove the panel menu ,
remove or  rename the icon-theme.cache file in /usr/share/icon/hicolor
add the panel menu to the panel again 

that might solve your problem

---

### Post by macewan on 2006-09-23
from commandline:

locate distributor-logo

my displays this:

/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
/usr/share/icons/hicolor/32x32/apps/distributor-logo.png
/usr/share/icons/hicolor/22x22/apps/distributor-logo.png
/usr/share/icons/hicolor/16x16/apps/distributor-logo.png
**/usr/share/icons/hicolor/24x24/apps/distributor-logo.png**
/usr/share/icons/hicolor/72x72/apps/distributor-logo.png
/usr/share/icons/Human/22x22/places/distributor-logo.png
/usr/share/icons/Human/24x24/places/distributor-logo.png
/usr/share/icons/Human/48x48/places/distributor-logo.png
/usr/share/icons/Tango/scalable/places/distributor-logo.svg
/usr/share/icons/Tangerine/scalable/places/distributor-logo.svg
/usr/share/icons/Tangerine/16x16/places/distributor-logo.png
/usr/share/icons/Tangerine/22x22/places/distributor-logo.png
/usr/share/icons/Tangerine/24x24/places/distributor-logo.png

assuming the file I want to replace it with is call bill.png, is in the same directory I'm currently in with the terminal and is 24x24, to replace hicolor 24x24 distributor-logo.png I do this:

sudo cp bill.png /usr/share/icons/hicolor/24x24/apps/distributor-logo.png

---


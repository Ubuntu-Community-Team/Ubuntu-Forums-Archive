---
title: "Menu size"
date: 2006-09-03
forum: Desktop Environments
---

### Post by alanh on 2006-09-03
Is it possible to change the size of the menu/toolbars (icon size, font size) in applications (Firefox, Open Office)?   I find the menu annd toolbars in Ubuntu take up more screen space than XP (for the same screen resolution) and I'd like to decrease it.

Thanks.

---

### Post by mssever on 2006-09-03
To change those, you need to change the theme. Go to System > Preferences > Themes, and choose a new theme. You can get new themes from gnome-look.org and art.gnome.org.

---

### Post by ayoli on 2006-09-03
you also can create a file in your home dir named .gtkrc-2.0 (don't miss the '.' at begining), edit it and add this line (change the values to what you want):
```
gtk-icon-sizes = "gtk-large-toolbar=18,18:panel-menu=16,16:gtk-menu=14,14"
```
then quit gnome session and log in again.
font size can be changed with gnome-font-properties which is accessible in menu System > Preferences > Font properties.

---

### Post by alanh on 2006-09-03
Thank you.  That's done the trick for the Ubuntu menu icons etc but doesn't seem to have done anything to modify the icon size in the Firefox toolbars, which is still larger than XP. I'd still like to reduce these if possible.  Anything I should add to the .gtkrc-2.0 file?

Cheers

---

### Post by bulldog on 2006-09-03
Open Firefox.
Go to view and toolbars and choose customize.
Pop up a menu where you can set Use Small Icons among other things :D 

Hope this will help you.

---

### Post by alanh on 2006-09-03
Thanks, I have small icons selected.  Unfortunately, they are still larger than in XP.

---

### Post by bulldog on 2006-09-03
I use the Vista 1.5 theme and they are quit small.

Only the page forward/backward are a little bigger,but that is in the theme.

Search for a new theme that suites you better.

You can also alter the menu bars to get a larger window with less bars in it.
There was a howto how you can alter it,I take a look if I can find it and post it here.

---

### Post by strabes on 2006-09-03
i dont even have any icons on my firefox. i took them all off cuz u dont really need them. ctrl+L goes to address, ctrl+k goes to search box, esc is stop, F5 is refresh, ctrl+f5 is refresh from server, and u can use a mouse gestures extension for everything else (switching tabs, back, forward, maybe refreshing, etc. yeah lol so my advice is get rid of the navigation toolbar and just drag the address and search bars up to the menu toolbar. gives you more screen area anyway........

---

### Post by alanh on 2006-09-03
Could you send me a link for the Vista 1.5 theme?  I've tried Googling it but I'm not sure which one you're referring to.

Cheers

---

### Post by grizzly on 2006-09-04
Use opera, 
very skinnable, and you can specify the exact percentage size of buttons plus tou can make buttons/shortcuts/mouse gestures/rightclick menu item to toggle toolbars :D .An example :: in the default installation click on thh 'glasses' icon

---


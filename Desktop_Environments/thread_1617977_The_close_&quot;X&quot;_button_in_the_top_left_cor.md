---
title: "The close &quot;X&quot; button in the top left corner on its own like AmigaOS"
date: 2010-11-10
forum: Desktop Environments
---

### Post by vaserlan on 2010-11-10
Is there anyway to have the close "X" button in the top left corner of each window on its own?  This would make accidental closings of windows less likely when the intent was just to restore/maximize. Mostly it would just speed things up I believe. 

So is there any way to have the close button in the top left corner of each window and to have the minimize and restore/maximize buttons remain in the top right corner of each window?

A similar approach was [and still is] used in AmigaOS.

---

### Post by Brandel Valico on 2010-11-10
1) Alt-F2 gconf-editor
2) Apps
3) Metacity
4) General
5) change button-layout to read as follows:

menu,close:minimize,maximize

That will place the Menu and close buttons on the left and the min/max on the right. Now mind you this does so on the current theme only so if you change your theme it may need to be done again.

If you don't wish to have the menu or any other button just delete it in the button-layout list.

To have all the buttons on the right just type 

menu:minimize,maximize,close

Of course to go back to the current Default type

close,minimize,maximize:menu

(I think thats the default I use the older right button setup myself)

---

### Post by vaserlan on 2010-11-10
> **Brandel Valico said:**
> 1) Alt-F2 gconf-editor
2) Apps
3) Metacity
4) General
5) change button-layout to read as follows:

menu,close:minimize,maximize

That will place the Menu and close buttons on the left and the min/max on the right. Now mind you this does so on the current theme only so if you change your theme it may need to be done again.

If you don't wish to have the menu or any other button just delete it in the button-layout list.

To have all the buttons on the right just type 

menu:minimize,maximize,close

Of course to go back to the current Default type

close,minimize,maximize:menu

(I think thats the default I use the older right button setup myself)

Thanks. :)

---

### Post by mcduck on 2010-11-10
You can of course also leave the "menu" away completely, it's not required and the same menu is accessible with a right-click on the titlebar anyway so you only need it if you want the program's icon to appear in the titlebar. :)

---


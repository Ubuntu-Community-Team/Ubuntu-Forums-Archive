---
title: "A few Xfce questions"
date: 2007-06-02
forum: Desktop Environments
---

### Post by CupofDice on 2007-06-02
Just installed xfce and it's pretty cool except for a few things.

1. Files on the desktop are copied to Thunar instead of being moved. Is that normal and can I change?

2. How do I add icons to my bottom panel (was the default top one) where the firefox and thunar are located. 

3. In gnome I had the xkill, and lock screen applets on the panel. Can I duplicate that here.

4. Does Xfce have something like Alacarte so I can hide some apps in the menu. ((( Just discovered this [http://ubuntuforums.org/showthread.php?t=421973&highlight=Customize+Xfce](http://ubuntuforums.org/showthread.php?t=421973&highlight=Customize+Xfce) ouch)))

5. How do I install themes and is there a gui way for it (doesn't exist right :( ).

Thanks for all help.:D

---

### Post by ugm6hr on 2007-06-03
> **CupofDice said:**
> Just installed xfce and it's pretty cool except for a few things.

1. Files on the desktop are copied to Thunar instead of being moved. Is that normal and can I change?

2. How do I add icons to my bottom panel (was the default top one) where the firefox and thunar are located. 

3. In gnome I had the xkill, and lock screen applets on the panel. Can I duplicate that here.

4. Does Xfce have something like Alacarte so I can hide some apps in the menu. ((( Just discovered this [http://ubuntuforums.org/showthread.php?t=421973&highlight=Customize+Xfce](http://ubuntuforums.org/showthread.php?t=421973&highlight=Customize+Xfce) ouch)))

5. How do I install themes and is there a gui way for it (doesn't exist right :( ).

Thanks for all help.:D

1. Not really sure what you mean by this.  Thunar is the File Manager - you can't copy anything *to* Thunar.  I believe files on the Desktop are in /home/_username_/Desktop if you want to access them in Thunar easily (there is a quick-link to Desktop on the left).

2. Right-click on the taskbar panel (top or bottom - wherever you want) and select Add New Item.  Further details here:
[http://ubuntuforums.org/showthread.php?t=448102](http://ubuntuforums.org/showthread.php?t=448102)

3. Don't know. But if they are applets, you should be able to run the applet from Terminal, and they should appear in the sys-tray (the same way GAIM / Network Manager does).  If it's just a taskbar "run" icon, then follow the advice in 2.

4. Not tried it, but apparently yes:
[http://wiki.xfce.org/tips#how_to_install_new_themes](http://wiki.xfce.org/tips#how_to_install_new_themes)

5. No idea.

More info here:
[http://www.xfce.org/](http://www.xfce.org/)

---

### Post by rax_m on 2007-06-03
>  Originally Posted by CupofDice  View Post
Just installed xfce and it's pretty cool except for a few things.

1. Files on the desktop are copied to Thunar instead of being moved. Is that normal and can I change?

2. How do I add icons to my bottom panel (was the default top one) where the firefox and thunar are located.

3. In gnome I had the xkill, and lock screen applets on the panel. Can I duplicate that here.

4. Does Xfce have something like Alacarte so I can hide some apps in the menu. ((( Just discovered this [http://ubuntuforums.org/showthread.p...Customize+Xfce](http://ubuntuforums.org/showthread.p...Customize+Xfce) ouch)))

5. How do I install themes and is there a gui way for it (doesn't exist right ).

Thanks for all help.




Hi there

1. That annoys me a bit as well.. but if you hold Ctrl  and then drag I think it moves the file. Otherwise if you right click&drag (has to be done quite quickly so the default right-click menu doesn't come up) you can specify to move, copy etc. 

3. Lock screen is added via the "add items to panel" diaglog. There is one item called "Action buttons" and u can customise whether it should be lock screen or log out. 


Sorry not sure about the others. 

Rax

---

### Post by CupofDice on 2007-06-03
1. Not a big deal.

2. Thanks ugm6hr for the link.

3. Seems that the shutdown applet can also lock the screen and I got a mini terminal for xkill.

Thanks for the help. Cheers:D

---

### Post by Koori23 on 2007-06-03
> **CupofDice said:**
> Just installed xfce and it's pretty cool except for a few things.

1. Files on the desktop are copied to Thunar instead of being moved. Is that normal and can I change?

2. How do I add icons to my bottom panel (was the default top one) where the firefox and thunar are located. 

3. In gnome I had the xkill, and lock screen applets on the panel. Can I duplicate that here.

4. Does Xfce have something like Alacarte so I can hide some apps in the menu. ((( Just discovered this [http://ubuntuforums.org/showthread.php?t=421973&highlight=Customize+Xfce](http://ubuntuforums.org/showthread.php?t=421973&highlight=Customize+Xfce) ouch)))

5. How do I install themes and is there a gui way for it (doesn't exist right :( ).

Thanks for all help.:D

1. I guess you mean, that when you drag and drop something from one folder to another, it just copies it instead of moves it. That is normal, I don't know how to fix it.

2. Right click and choose "Add Item". Then while that screen is open, on your XFCE Menu, choose Accessories, AppFinder. Drag the icon of the program you want into that "Add Item" box, it'll fill in the program path automatically. Follow these steps for as many icons as you want.

3. You could create a shortcut for this.. Just "Add Item" again and manually create an icon. Try XKill or sudo shutdown.allow -a now 

4. Yes, in the XFCE Menu, Choose "Settings" then Menu Editor.

5. No, we don't have  GUI assist for installing themes. we must manually extract the items to /usr/share/themes

---

### Post by Bruce McGoose on 2008-07-01
Old thread, but found this while googling for an answer.. so thought posting here could be useful for someone else.

for 1) shift + drag seems to work.

---


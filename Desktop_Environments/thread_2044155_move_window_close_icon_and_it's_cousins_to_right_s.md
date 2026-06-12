---
title: "move window close icon and it's cousins to right side"
date: 2012-08-18
forum: Desktop Environments
---

### Post by RogerDavis on 2012-08-18
I'm using the Gnome version from the Software Center.  I want to move the window closing, enlarge, etc. (X, _, and []) icons to the right side of the screen, and maybe color the X one red.

How can either / both of these things be done?

Thanks!

---

### Post by zombifier25 on 2012-08-18
Type this command:
```
gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close
```

---

### Post by OM55 on 2012-08-19
I suspect the gconftool will not work with Ubuntu 12.04 for this but only on previous versions.
However, you can always use ubuntu-tweak move the close/minimize/maximize icons to the right.

1. Download Ubuntu Tweak from [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

2. If it was not added to the menu automatically, launch by typing in terminal:
```
ubuntu-tweak
```3. Click on 'Tweaks' tab

4. Select 'Windows'

5. Change the top option as you like: 'Window control button position'

That's it. Hope this helps!

---

### Post by RogerDavis on 2012-08-19
OK, Ubuntu Tweak did the job.  

However, it has to be launched from Terminal, it didn't show up in any menu I can find.

How can I get it into a menu?  

Where did it get installed to ?

---

### Post by OM55 on 2012-08-19
If you use Unity, there is no menu option... but if you use gnome-session-fallback (or any other version of the gnome 3 classic menu), here is what you need to do to make Ubuntu Tweak appear on the menu:

1. Applications -> System Tools -> Preference -> Main Menu
(alternatively, you can also open terminal and type: alacart )

2. Click on 'System Tools' on the left pane

3. Click on 'New Item' button (top right of the window)

4. For 'Name' enter: Ubuntu Tweak
    For 'Command' enter: ubuntu-tweak
If you entered the command correctly, as soon as you move the cursor to a different entry field, the default icon should change to the Ubuntu Tweak icon

5. Click 'Ok' and close the application.

Now you should have 'Ubuntu Tweak' option in the main menu under Applications -> System Tools.

(If that solved your problem, please mark this thread as 'Solved').

---

### Post by RogerDavis on 2012-08-19
Got it done, but the following adjustment was needed :

2. Click on 'System Tools' on the left pane, [COLOR="Blue"]click on "Preferences" under "System Tools"[/COLOR]

If this isn't done, it ends up under "System Tools".

Thanks!

---

### Post by bob-linux-user on 2012-08-19
MW Buttons will also do it

[http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html](http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html)

---

### Post by bob-linux-user on 2012-10-29
Update: MWButtons does not work on 12.10. (so for me it is off to the MATE desktop environment)

---

### Post by bob-linux-user on 2012-12-07
Luckily I found this solution

[http://handytutorial.com/move-window-buttons-to-right-in-ubuntu-12-10-12-04/](http://handytutorial.com/move-window-buttons-to-right-in-ubuntu-12-10-12-04/)

so my defection to Linux Mint is postponed.

---


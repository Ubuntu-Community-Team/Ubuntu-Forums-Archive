---
title: "How to have XP style Start Menu"
date: 2009-09-19
forum: Desktop Environments
---

### Post by tomcatProb on 2009-09-19
Hi,
How can i have XP style Start Menu in Ubuntu. Curentky all program are shown in the Application menu which is at the top most part of the screen. Pls help.

---

### Post by TheConsaw on 2009-09-19
install the KDE desktop

---

### Post by scragar on 2009-09-19
Of you could remove the current menu and add the one called "main menu" rather than the custom menu. That looks more like the windows menu without a reinstall.

---

### Post by Chronon on 2009-09-19
You can put the panel along any edge of your screen.  Add a new panel to the bottom and put whatever you want in it.

---

### Post by OxR on 2009-09-21
sudo apt-get install kubuntu-desktop

---

### Post by Enigmapond on 2009-09-21
But...why would you want that?...eh bien. C'est la vie. The above install will give you something similar to XP..

Cheers!

---

### Post by lisati on 2009-09-21
There's always this thread: [http://ubuntuforums.org/showthread.php?t=821146](http://ubuntuforums.org/showthread.php?t=821146)

I think it's geared to a setup with the KDE desktop, as used by Kubuntu.

---

### Post by gadolinio on 2009-09-22
-Right click the ubuntu icon on the top-left corner, then click "quit from panel". Then right click that part of the panel and select "add to panel". Choose "main menu", click "add". That will give you a single-button menu, more like the one of windows. You can also add that main menu to the lower panel, as in windows.

-To have it to show another icon:
add the image you want there in /home/YOUR_USER_NAME_HERE/.icons/ICON_THEME_YOU'D_LIKE_TO_USE/scalable/places; name that image "start-here.png". When you choose to use that icon theme (in system-->preferences-->appearence), the image you put in the file "start-here.png" will be the logo for the main menu. If you are using an icon theme which is not in your user folder, but in a system one (/usr/share/icons/WHICHEVER_ICON_THEME_YOU'RE_USING), copy that folder ("whichever_icon_theme...") to /home/your_user_name/.icons, and then implant the start-here.png file in /home/user_name/.icons/copied_icon_theme/scalable/places. And choose to use that icon theme.
I've done this succesfully several times. Reply if you have any trouble.
Hope you find this useful!

PS: if the image is taller than 48 pixels (or 50, something like that), the panel bar where the menu is will increase its width, and it could be somewhat ugly maybe. If you don't like it visually, resize the image. You don't need to put anything huge there, anyway; just the windows flag if i got it correctly.

PS(2): if you make any changes to the star-here file, you'll see they don't apply immediatly when you save them. You'll have to open  system-->preferences-->appearence to have it refreshed. If it still doesn't change, switch to another icon theme and re-switch to the one you're modifying. Then you'll see the menu logo change.

---


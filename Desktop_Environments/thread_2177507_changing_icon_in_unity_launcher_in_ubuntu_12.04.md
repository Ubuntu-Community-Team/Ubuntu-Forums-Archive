---
title: "changing icon in unity launcher in ubuntu 12.04"
date: 2013-09-29
forum: Desktop Environments
---

### Post by sandeep9285 on 2013-09-29
How can i change unity launcher icons in ubuntu 12.04??? Eg: how to change Files icon in unity launcher in ubuntu 12.04??????

---

### Post by Frogs Hair on 2013-09-29
For applications I use the main menu . If you have the Gnome Fallback Session installed you already have this application and if not use the following command which installs the main menu without the Gnome Session  . ```
sudo apt-get install --no-install-recommends alacarte
``` When opening the main menu enter the applications properties by right clicking on the line where is a appears . A dialog box will appear , select the icon image on the left side and navigate/browse to any folder with an image you would like to use . Select the image and select open. The new icon won't appear immediately and I usually remove the application from the launcher and open the application again and when the new icon appears , just lock it to the launcher. There are other methods , but I haven't used them.

---

### Post by stinkeye on 2013-09-29
...adding to **Frogs Hair**'s post....
what your actually doing is copying the applications .desktop file from **/usr/share/applications** to **~/.local/share/applications**
with an added line for the new icon location.

Desktop files in **~/.local/share/applications** will override the ones of same name in **/usr/share/applications**.

This is another way of editing a launcher if say you wanted to make your own quicklist item.
eg I use nemo as my main file browser and just added quicklist items to launch nautilus and clear recent.
[ATTACH=CONFIG]246623[/ATTACH]

Open gedit , search in the dash for the application you want to edit and 
drag and drop it from dash to the gedit window.
Make your changes to the .desktop file then in gedit... File > save as.....and save to **~/.local/share/applications**
Removing the .desktop file from **~/.local/share/applications** will revert to using the default in **/usr/share/applications**.

---


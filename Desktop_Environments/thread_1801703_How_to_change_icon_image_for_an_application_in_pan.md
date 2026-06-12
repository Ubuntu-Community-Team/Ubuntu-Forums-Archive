---
title: "How to change icon image for an application in panel"
date: 2011-07-11
forum: Desktop Environments
---

### Post by GregA on 2011-07-11
Hi,

I recently decided to try Kubuntu 11.4 and it's been a long time since I've used KDE.

The first application I installed in Kubuntu was Treeline,, a database, info manager that I keep all kinds of useful and sensitive data.   The standard icon image in Treeline is a png file that depicts two pine trees.  

For whatever reason, the install via the K package mgr didn't set that up, and I would like to replace the rather plain image with the original image.   I've searched and have not found a method in KDE (like updating the launcher in Gnome).

Any tips or info appreciated.

---

### Post by uRock on 2011-07-11
Bump for move to *Desktop Environments*.

---

### Post by ankspo71 on 2011-07-11
Hi,
I'm sure there is a another way to do it (probably by editing a xxxxx.desktop file or kde config file somewhere in your hidden ".kde" directory), but what I do is I change the icon to the application in the start menu first, then I right click on that modified start menu entry to add the application to the panel second. It will then add the shortcut to the panel using the new icon. 
Hope this helps.

PS. You will have to unlock your widgets before you will be able to add shortcuts from the start menu to the panel.

---

### Post by GregA on 2011-07-11
Well OK, I can't yet find a way to edit the K Menu, and/or the individual applications within it.   Is there some way to get a "properties" like dialog box, that has a file navigator/selection tool within it?   It seems it shouldn't be this complex.  Also, right clicking an application icon in the panel, and then clicking on "icon settings" doesn't have an intuitive way to change the icon (in Gnome,, the user can just click on the icon image to get set of dialog windows to change it)

---

### Post by ankspo71 on 2011-07-12
Hi,
Right click on your start menu icon then choose Edit Applications.

Then when the start menu editor opens, find the entry for treeline and click on it to edit the entry. The properties will be shown.

In the properties, click on the current Treeline icon to select another icon. 

If you want to use a system icon, you have a preview window to look through and several categories to choose from in a drop down menu.

If you want to use your own custom icon, click on the 'other icons' button then use the browse button to look for the icon file on your hard drive.

When you are done selecting an icon, click on the save button in the start menu editor.

Now go back to the start menu and find treeline. When you find it, you should see that it is using your new icon. Right click on it and choose 'add to panel'. 

If it does not give you that option, then right click on the start menu again and choose 'unlock widgets', then try again.

---

### Post by lkraemer on 2011-07-13
While I'm running Debian 6.0 (Gnome) the same methods apply for your Icon search.  Open a Terminal
Window (Console) and search for the Icons locations.  There will be many, but most are located in
the subdirectories around (and further down the subdirectory tree):
```

/usr/share/icons/
/usr/share/icons/hicolor/48x48/apps/firefox.png

```

To search for all *.png files do:
```

cd /
sudo updatedb
locate *png
locate *png > searched.txt
locate *png | grep firefox
exit

```

Then you can search the txt file for any entry you want.  Or you can use
grep to assist in your searches.
```

locate *png | grep firefox

```
Which finds the following:
```

/home/larry/Firefox-Icon/firefox.png
/usr/share/icons/HighContrastLargePrint/48x48/apps/firefox-icon.png
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/firefox-icon.png
/usr/share/icons/hicolor/48x48/apps/firefox.png
larry@debian:/$

```

lk

---

### Post by GregA on 2011-07-13
Anksop71 and IKraemer:

Thank you both!  Each solution works great and will be added to my "Treeline" database "Linux Tips" . . . . For the newer KDE users, I wish the developers would have put the menu edit options  within the Systems Settings selections.  

Thanks again . . . .

Greg

---


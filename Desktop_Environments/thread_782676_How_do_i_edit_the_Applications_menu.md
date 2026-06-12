---
title: "How do i edit the Applications menu?"
date: 2008-05-05
forum: Desktop Environments
---

### Post by kripz on 2008-05-05
Edit menu only lists

Settings
Help
About XFCE
Quit

I want to add/remove some short cuts.

---

### Post by Arasfang on 2008-05-05
Right click "Applications" in menu and choose "Edit Menus"

---

### Post by kripz on 2008-05-05
Edited original post to clarify.

---

### Post by WinterWeaver on 2008-05-05
System >> Preferences >> Main Menu

just tick the boxes to hide/show them

right-click to view/edit the command, description icon etc.

EDIT: Whoops... only now noticed you're on XFCE.... sorry instructions was for normal ubuntu

---

### Post by Bluekkis on 2008-05-05
You can also make adding new programs bit easier by using xfce4-appfinder, just find the application there and drag'n'drop into menu editor.

---

### Post by kripz on 2008-05-05
Yeah adding things is easy but removing things is bugging me. Perhaps i should do it manually? there should be a config somewhere.

---

### Post by kripz on 2008-05-07
bump

---

### Post by Person98 on 2008-05-07
if you just want to add some shortcuts go to settings-->settingsmanager then select menu editor. click add new entry, select launcher type in the command and name. hope it helps best of luck. you can add the shortcuts anywhere you want to the menu(use the up and down arrows) you can also add sub menus and separators. All of the default shortcuts appear as "include system" and you can edit them with the gnome menu configuration utility

---

### Post by kripz on 2008-05-08
I want to remove things.. as stated numerous times.

---

### Post by ingvildr on 2008-05-08
Xfce auto generates its menu from the .desktop files it finds in /usr/share/applications and maybe from other places, you would either have to edit individual .desktop files or remove the green applications entry in the menu editor and make a menu from scratch.

Or if Xubuntu does it differently i dont know, it may have different files for different parts of the menu so you have have to right click on applications go to properties/ preferences and see if its pointing to a different file, then edit that one.

---

### Post by oomlout on 2008-05-19
All the info I've been able to find about editing the "desktop menu" is actually about editing the "Applications menu". I.e. it starts by assuming you get the same set of options when right-clicking on the desktop as you do when clicking on the "Applications" menu on the top panel.

But that's not what I got by default.  I get a different menu when I right-click on the desktop:
[INDENT]  Create Launcher...
  Create URL Link...
  Create Folder...
  Create From Template
  ---------------------------
  Desktop Settings...
[/INDENT]
I know I can get the applications menu to show up instead, but I don't want to.  I want to edit the menu I get now.  How can I do that?  It doesn't appear to be related to menu.xml at all.


--Andy

---

### Post by kripz on 2008-05-19
Read ingvildr's post. You have to create/edit the desktop files.

---

### Post by denham2010 on 2008-05-20
Hi,

Menu's in XFCE only have the main menu editor, which you primarily use to create a brand new menu. To add and remove items in the existing (default) structure is not catered for with an XFCE GUI.

There are several ways to easily add and remove items to the existing menu structure:

1. Install alacarte. This is the Gnome menu editor. It will bring a lot of Gnome dependencies with it though (so avoid this option if you only want pure XFCE). With alacarte, you can locate the items you no longer want shown (remember, this will show the Gnome menu structure, so items may appear under different categories eg Internet instead of Network) and just untick them. This will remove them from the XFCE menu.

2. If you don't want to install alacarte, the next easiest way is manual (no gui) but is not too difficult. Firstly you need to locate the .desktop file for the item(s) you wish not to appear in the menu. As in previous posts, they will most likely be in /usr/share/applications, the other location you will most likely find them is /home/username/.local/share/applications. Once you have found the .desktop file open it in mousepad (if it is in /usr/share/applications you will need to open it as root) and find the following line:

```
NoDisplay=false
```

and change it to

```
NoDisplay=true
```

If the line does not exist in the file, just add

```
NoDisplay=true
```

to the end of the file and save it.

The file will no longer appear in your menu. If you wish to turn it on again later, just change the line to

```
NoDisplay=false
```

3. The last way is through the XFCE menu editor. This will require you to make a completely new menu. Once the menu editor is open, select FILE - NEW. This will ask you if you wish to close the current menu (probably best to do a FILE - SAVE AS first to back up the default menu). Select YES and now you can create a menu structure as you wish. Once this is done, you can easily add and remove items from this gui as you please.

Personally, I use alacarte, as I simply couldn't be bothered creating my own new menu structure. You will find though, that adding items through alacarte will make the items appear in the OTHER menu in the XFCE default menu. To correct this, as in option 2 above, locate the .desktop file and find the following line:

```
Categories=GNOME;GTK;Settings;
```

(The items after the = will vary depending on the item)

Just add to the end of this line the name of the XFCE menu category(s) you wish it to appear under ie: Graphics, Multimedia, Network etc. and end the line with a semi colon. eg:

```
Categories=GNOME;GTK;Settings;Network;
```

The item should now appear in under the menu item of your choice (Network in the above example).

So as you can see, it's not the most user friendly way to manage a menu, and by far, the simplest way is using the XFCE gui (the only hassle is the initial menu creation).

Hope this helps, and please ask ore questions if any of this is not very clear (I am so bad at explaining things!)

Cheers!

---

### Post by ErwinC on 2008-05-23
I found this [here](http://wiki.xfce.org/faq)

> How to edit the auto generated menu with the menu editor?

cp ~/.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ~/.config/xfce4/desktop/menu2.xml
cd ~/.config/xfce4/desktop/
cat menu.xml > menu3.xml
cat menu2.xml >> menu3.xml
mv menu.xml menu.orig.xml
mv menu3.xml menu.xml

Now, you already have a menu with all the categories in the main tree with some duplicates, but you must first edit menu.xml with your favorite editor and remove the 4 following lines in the middle of the file, otherwise the menu editor will complain about a wrong format:

</xfdesktop-menu>
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xfdesktop-menu>

<xfdesktop-menu>

That's all. Now you can run the menu editor, remove the few duplicates and edit all as you like.

Settings > Desktop > Menu > Menu Editor

Notes: by removing the &#8220;system&#8221; line, you will remove all the duplicates menu entries from the auto generated file. So, if it is changed in this auto generated file, they don't appear anymore, but you will get rid of most of the duplicates.

To restore the original menu, just do in a terminal:

mv menu.xml menu3.xml; mv menu.orig.xml menu.xml

It worked for me.

Erwin

---

### Post by cogadh on 2008-11-23
I hate to resurrect an old thread, but I am having similar issues with XFCE right now. My problem is I have several menu entries popping up under "Other" because they are actually in sub-menus that XFCE can't see for some reason. Specifically, these are apps installed through Wine. The main Wine menu appears fine, but the Programs sub-menu and all other sub-menus under that fail to appear. I have looked at the .desktop entries for the apps I have installed through Wine and I don't see how I can get the XFCE menu to see the sub-menus these apps should have. Here's an example of one of the desktop entries I am talking about:
```
[Desktop Entry]
Name=Notepad
Name[sv]=Anteckningar
Name[de]=Editor
Name[fi]=Muistio
Name[pl]=Notatnik
Name[ca]=Bloc de notes
Comment=A clone of Windows Notepad
Comment[sv]=En klon av Windows Anteckningar
Comment[de]=Ein Windows Editor Klon
Comment[fi]=Windows Muistio -klooni
Comment[pl]=Klon Notatnika Windows
Comment[ca]=Un clon del Windows Notepad
Exec=notepad
Terminal=false
Type=Application
Icon=wine-notepad
Categories=Wine-Programs-Accessories;
```
I assume the problem comes in on the "Categories" line. XFCE doesn't seem to understand that "Wine" should have a sub-menu called "Programs" which should have a sub-menu called "Accessiories" which is where the shortcut for Notepad should be. Is there any way to fix this? I don't want to use the method ErwinC posted, as doing that will require me to manually re-merge the menu every time I install or uninstall something with Wine, I would rather have a way that lets XFCE see the menus as they are already being created.

---

### Post by cogadh on 2008-11-24
Hopeful bump...

---

### Post by cogadh on 2008-11-25
Now its a desperate bump...

---


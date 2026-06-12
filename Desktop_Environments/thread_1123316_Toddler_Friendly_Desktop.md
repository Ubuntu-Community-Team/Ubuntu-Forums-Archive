---
title: "Toddler Friendly Desktop"
date: 2009-04-12
forum: Desktop Environments
---

### Post by hartz on 2009-04-12
Good day,

I need a way to set up a toddler friendly desktop.  Basically I want to set up an environment for my son which can launch only the games.  The icons and fonts must be huge, the mouse pointer too.

Any hints and suggestions!?

---

### Post by ad_267 on 2009-04-12
This all assumes you're using the default Gnome desktop.

You can set the fonts to large sizes in System - Preferences - Appearance - Fonts. The mouse size can be changed by going to the Theme tab, selecting Customize and then changing the size in the Pointer tab.

You can edit what shows up in the menu by right clicking on it and selecting Edit Menus. You can also drag launchers onto the desktop then right click and select Stretch Icon to make them larger.

---

### Post by sekinto on 2009-04-12
Make an account for your child and log in under that name.

Add a logout and shutdown launcher (icon) to the desktop along with all the game launchers you want (you can do this by dragging them from the menu to the desktop. Rescale and rearrange them how you want.

Then press Alt+F2 and type gconf-editor and press Enter.
Navigate to /desktop/gnome/session (select the folder that says session).
On the right double click the required_components_list attribute.
Select panel and then click Remove and then OK.

Edit IMPORTANT:
Navigate to /apps/metacity/general (select the folder that says general).
On the right double click the button_layout attribute.
Change the value to menu:maximize,close and then click OK.

Exit gconf-editor.

Log out and log back in.


Edit:
Forgot to mention what this will do.
When your child logs in they will be presented with a blank panel-less desktop with just the huge launchers on it. Also the minimize button will be removed from the windows, there really is no point in minimizing windows if there isn't a panel to unminimize them with (and your child probably doesn't know about alt-tab).

---

### Post by hartz on 2009-04-12
Hello all.

Thank you for the suggestions so far.  I am using gnome, but I am open to suggestions for alternatives.

I have the Menus trimmed down and the fonts and colors set to what I want.

I don't know where to find an option to change the spacing and/or size of desktop icons, and the option to change the mouse cursor size appears to be broken (The cursor size slider have no effect, even if I put it all the way to the maximum side).

Some other things I am thinking of is to create a backup of the user home directory (once I get it configured the way I want it).  Ideally I would like this backup be restored automatically on every login (after entering the password, but before reading the desktop configuration!?).

Another option would be to set certain directories to be read-only,  particularly the user's ~/Desktop directory, to prevent accidental removal of icons, etc.  In fact it might be better if I could make gnome ignore the "Delete" button all together.

Another questions:  I am looking for really simple games.  Eg just wack space bar to "wack" the face that pokes out of the hole.  Mouse and other keyboard keys will follow soon.

Right now "text editor" is my son's favorite application (hurray for full screen mode!)

Again, thank you for the suggestions so far!

P.S. I've just found the "Sugar" GUI... will look at whether this is any good!

---

### Post by sekinto on 2009-04-12
You resize an icon by right-clicking it and then click Stretch Icon.

If you don't want your child to be able to mess with a certain folder or file (like Desktop) you can run nautilus as root:
[Alt+F2] gksudo nautilus [Enter]
Then browse to the folder/file and right click it and go to preferences.
Go to the permissions tab and change the owner and group to root and give the owner and group "create and delete files" and "read and write" permissions, but only give other "access files" and "read" permissions.
Although you do not want to do this the their whole home directory because this would prevent them from saving games and would cause a bunch of other permissions issues.

---

### Post by ad_267 on 2009-04-12
> I don't know where to find an option to change the spacing and/or size of desktop icons, and the option to change the mouse cursor size appears to be broken (The cursor size slider have no effect, even if I put it all the way to the maximum side).

Open the file browser and go to Edit - Preferences - Views and you can change the default zoom level of icons. This will also affect icons on the desktop. You can also stretch individual icons like we said before. You probably have to select a cursor other than the default. If there aren't any other options available then install some from the package manager, eg. "dmz-cursor-theme" or "oxygen-cursor-theme".

> Another option would be to set certain directories to be read-only,  particularly the user's ~/Desktop directory, to prevent accidental removal of icons, etc.  In fact it might be better if I could make gnome ignore the "Delete" button all together.

I don't know about ignoring the delete button but it would be easy enough to make the desktop and any other directory read only.

---

### Post by hartz on 2009-04-12
It would appear that some of the Mouse Cursors allow themselves to be resized, while others simply does not.

I am currently evaluating the games, themes, etc.  It is a lot of work to go through everything!

:guitar:

While the profile for my son is now more or less functional, I will keep monitoring this thread for suggestions!

Again thank you all, the suggestions has been very helpful!

---

### Post by sekinto on 2009-04-12
Your child may like the games SuperTux and LBreakout. When I was a child two of my favorite games to play on the NES were Super Mario Bros and Araknoid, which those two games are similar to.

---


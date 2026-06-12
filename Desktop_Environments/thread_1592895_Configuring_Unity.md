---
title: "Configuring Unity"
date: 2010-10-11
forum: Desktop Environments
---

### Post by nkealen on 2010-10-11
I've been searching all over ubuntu-land the last two hours for anything about configuring Unity and I'm coming up a little short. Can anybody point me to some documentation that I may have missed?

I figured out how to pin apps to the sidebar, but I'd like to configure the "Favorites" folders and just see what other options can be customized.

I would have thought right-clicking (anywhere) would have helped, but I get nowhere.

---

### Post by kerry_s on 2010-10-11
it's to new to find anything useful on the net.

what favourites? there is no favourites section in 10.10.
do you you mean most used?

---

### Post by artAlexion on 2010-10-13
Other than adding, removing, and reordering the icons on the side, is there any way to configure it?  

For instance, I want to remove or clear the recently used section of files and folders.  It is an important privacy issue.  Can I do that?

I prefer a wider screen.  Can I move the icons to the top or bottom instead of the left?

In previous versions, I rarely left the favorites tab.  Is there a way to bring that back?  The gnome menu editor still sees it.

I don't mind messing with text or xml files.  I'd prefer not switching to KDE to accomplish this.

---

### Post by demauk on 2010-10-16
I found the xml file where Unity's menu is saved, but I could not successfully add another app :(

/home/alejandro/.gconf/desktop/unity/launcher/favorites

That folder has many app-xxx.desktop folders and one %gconf.xml. The xml has one entry per item in the Unity panel, including the Ubuntu button ("ubiquity"), and those entries make reference to the app-xxx.desktop folders.

Inside each app-xxx.desktop folder there's another %gconf.xml, and that file may point to a *.desktop file. For example, app-gnome-terminal.desktop/%gconf.xml has a string entry with value gnome-terminal.desktop.

Unfortunately, like I said, I was not able to create a new entry that worked.

---

### Post by kerry_s on 2010-10-16
put:
```
rm -f $HOME/.recently-used.xbel
```

in ~/.profile

---

### Post by artAlexion on 2010-10-19
> **kerry_s said:**
> put:
```
rm -f $HOME/.recently-used.xbel
```

in ~/.profile

Well, thanks.  That is certainly a partial workaround.  it insures that the favorites are removed each time ***I*** login.  It does not address the problem of stopping the save in the first place.  It also doesn't remove them if I log out and *another* user logs in.

I suppose I could also save the command as a script and have cron delete it periodically, which is a little bit better.  

There really *should* be a way to disable its creation in the first place.

---

### Post by kerry_s on 2010-10-19
in gconf-editor there is a setting for gedit, maybe that.

---

### Post by jalar on 2010-10-21
> **demauk said:**
> I found the xml file where Unity's menu is saved, but I could not successfully add another app :(

When I want to add an app, I start the app and drag the icon to a new place in the menu. When I close the app, the icon remains in the new place, and can be started from there.

---

### Post by chrisamiller on 2010-10-21
```
rm -f $HOME/.recently-used.xbel
touch $HOME/.recently-used.xbel
chmod ugo-rwx $HOME/.recently-used.xbel

```
This way, the file exists, but is empty and programs can't overwrite it.  Thus, your recently-added list is always empty.

---

### Post by AlexAv on 2010-10-21
The way I found to add some launchers was this...

I log in in the GNOME mode (it can be reached via this... before login in the below menu select GNOME) then once in the gnome I add the application launcher to the panel or to the taskbar, with the right click on the mouse over the normal menu application (It will appear beside the menus or the clock)... Log out and change again to Netbook edition at log in and once I run the application again and the launcher appears at the unity launchers bar now I'm available to via right click add it to the taskbar... 

Hope this helps a little and be understood. :)

---

### Post by bullium on 2011-05-13
> **chrisamiller said:**
> ```
rm -f $HOME/.recently-used.xbel
touch $HOME/.recently-used.xbel
chmod ugo-rwx $HOME/.recently-used.xbel

```
This way, the file exists, but is empty and programs can't overwrite it.  Thus, your recently-added list is always empty.

Really elegant and simple workaround chrisamiller; I like it! 

I would also have to agree with everyone else, Unity seems very lacking in configurability. I don't really see a point in locking the Untiy panel to the left side of the monitor. The ability to move the panel and or configure seems to me like should be the first menu's and or functionality that should have be developed.

---

### Post by mgmiller on 2011-05-14
> **bullium said:**
> Really elegant and simple workaround chrisamiller; I like it! 

I would also have to agree with everyone else, Unity seems very lacking in configurability. I don't really see a point in locking the Untiy panel to the left side of the monitor. The ability to move the panel and or configure seems to me like should be the first menu's and or functionality that should have be developed.

Actually, you can move them around.  Install ccsm and then look in the Ubuntu Unity Plugin.  In the Behavior tab, the first item is Reveal Mode.  This is what sets where the launcher is.  If you move it, you will have to change a few other things, but it will prompt you about them.  

In the Experimental tab, you can change other things like opacity in the top panel and also the way the icons in the launcher look and  behave.  I have the backlight mode set to backlight toggles.  You can also set the launcher icon size and other things from here.

The more I mess around with Unity, the more I find I can bend it to my will.  It is configurable.

Look at this site for lots of things to tweak in Unity:
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---


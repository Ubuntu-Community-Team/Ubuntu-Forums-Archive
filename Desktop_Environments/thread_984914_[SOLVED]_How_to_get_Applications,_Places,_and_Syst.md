---
title: "[SOLVED] How to get Applications, Places, and System into a desktop oren right-click"
date: 2008-11-17
forum: Desktop Environments
---

### Post by capleton on 2008-11-17
Is it possible to get the Applications/Places/System menus to appear in either left-click or right-click menus?

In other words, get them to appear as either a pop-up menu when there is a left-click in free space on the desktop; or as another menu entry(or entries) under the right-click menu (along with "create folder," "create launcher," etc.)



I tried installing enlightenment, but it doesn't work with compiz :(   I also tried tweaking "nautilus actions configuration," but no luck there either.  Is there another window manager that I could switch to that would give this kind of function?

Thanks!

---

### Post by ajgreeny on 2008-11-17
I think xfce does this by default, but I don't know if you can get the same action into the gnome desktop.

---

### Post by capleton on 2008-11-17
Thanks for the response :)

I got xfce from the repository and tried it out, so far I love it!
I might just stick with it and get rid of GNOME.  The only thing I'm going to miss is the world clock with the different time-zones that GNOME has.

I also found [this]("http://ubuntuforums.org/showthread.php?t=874458") thread.  It was tough to find, but very helpful.  I got the menus working through compiz, but there is a [this]("http://gitweb.compiz-fusion.org/?p=users/smspillaz/desktopclick;a=summary") link to how to get it working with left-click on the desktop, but I cannot get it working:

I installed into a directory entitled desktopclick, but when I give the command 'make,'```
~/desktopclick$ make
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
```


Any advice?

---

### Post by capleton on 2008-11-18
[SIZE="7"]SOLVED[/SIZE]

Ok, here is how to get a right click menu on the desktop with all of the functionality of the traditional right-click menu as well.

First portion is from Quazi:

> 
compiz-deskmenu


Obviously compiz needs to be running for this to work and a few packages are necessary beforehand.

Open a terminal and enter

```
sudo apt-get install python-lxml libgtk2.0-dev libwnck-dev libdbus-1-dev git-core compizconfig-settings-manager libdbus-glib-1-dev
```

Now enter

```

 cd ~
 git clone git://anongit.compiz-fusion.org/users/crdlb/compiz-deskmenu
 cd compiz-deskmenu
 make
 sudo make install
```

To make this menu show up we need to make some changes in the compiz settings. To bring this up, simply open a terminal and enter

```
ccsm
```

Now we just need to map this to the right mouse button. When in ccsm, click on general options and go under the commands tab and commands dropdown menu. Click on one of these that's unused and set it to compiz-deskmenu. Now go to Viewport switcherand set the Plugin for initiate action to core and the action name for indiate to run_command0_key. Change initiate plugin action key to Button 3 and now the right mouse button should popup the compiz deskmenu. If you'd prefer to keep the gnome right click menu, just leave initiate plugin action as button 2. To edit the menu, just click on the edit item in the menu.

One quirk I've noticed with the menu editor is that icons need to be located under /usr/share/icons/gnome/yyxyy where yy is the pixel size of the icon and for xpm files, this size needs to be set to 16x16 pixels (easily done with gimp) to be the same size as other menu items.

Next, you want to download some icons for the new menu items.  gnome-look.org

Then in the righclick menu that now pops up on the desktop, add a new launcher, call it "Nautilus Menu" or "Preferences" or whatever.  And for command enter ```
gconftool-2 --set /apps/compiz/plugins/vpswitch/allscreens/options/initiate_button --type string "Button2"
```.  
This will revert to the old menu.

To switch back to the new menu from this nautilus menu, you have to add a Nautilus Script.  Open a terminal and enter
```

cd ~/.gnome2/nautilus-scripts/ 
gedit Menu
```

This will bring up a blank document, enter ```
gconftool-2 --set /apps/compiz/plugins/vpswitch/allscreens/options/initiate_button --type string "Button3"
``` and save the document and exit.  Go back into the terminal (making sure your are still in "~/.gnome2/nautilus-scripts/") and enter ```
chmod +x Menu
``` to make it executable.

Now when you right click in nautilus, you will see a new script that will change the menu back.

(If anyone know how to do an "if/else" command so that this script only appears in the menu on the desktop, please let me know.)

Thanks

---


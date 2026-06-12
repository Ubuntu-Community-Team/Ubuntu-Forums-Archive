---
title: "How to edit main menu"
date: 2011-11-01
forum: Desktop Environments
---

### Post by mr.suchy on 2011-11-01
Hi everyone!

I just had install xfce and I have one simple question. How can I edit main menu ? I want to remove, add some application but I don't know how. I check web about this issiue but i don't want edit xml in several places.

Regards!

---

### Post by alco75 on 2011-11-01
If you look [here]("http://wiki.xfce.org/howto/customize-menu") you'll find a link to **LXMenuEditor** which, apparently, works with both LXDE and XFCE.

Cze&#347;&#263;

---

### Post by alco75 on 2011-11-01
Having said that, if you've installed XFCE on Lucid, it might not work as it says it requires XFCE 4.8 and I don't know what version is packaged under Lucid.

---

### Post by gsmanners on 2011-11-01
Yeah, Lucid (10.04) uses Xfce 4.6. I don't recall how that menu works, but I think it is different from 4.8.

---

### Post by mr.suchy on 2011-11-02
Hi,

Once again. I decide to install xubuntu with XFCE 4.8 (I think) but I have one problem. When I click on the main menu I don't have any item when I use a default menu. Why is that ?

Best regards!

---

### Post by LewisTM on 2011-11-02
Run
```
sudo apt-get --no-install-recommends install alacarte
```
inside a terminal window

This will install the standard Menu Editor without all of the other GNOME tools
Then right-click on the XFCE Applications button, choose Properties and Edit Menu

---

### Post by mr.suchy on 2011-11-02
@[LewisTM]("http://ubuntuforums.org/member.php?u=680986") thanks for quick replay. I had already install this tool. When I set a default main menu and click "edit menu" - xbuntu display default menu editor (gnome I think). But when I check or uncheck some iteam in menu and next click save or even reset. Xbuntu doesn't display anything and I don't know why ?? Sorry for my language.

Best regards!

--edit

This editor look look the same like this: Applications->Settings->Main Menu

For now I just install lxmed and then I set my own menu from /etc/xdg/menus/application.menu. Then I edit it from lxmed. But this is one problem I can't see all ow my application :/

---

### Post by doktorOblivion on 2012-09-17
This is one of the most frustrating problems with XFCE, lack of coherent tools.  I had a similar problem trying to go into properties->Main Menu and I was not seeing items in the list that were showing up in my menu.  Then for what ever reason I decided to:
```

sudo /usr/bin/xfce4-panel restart

```
This restarted a new instance of XFCE Panel that took precedence over the currently running one, since it was started as root.  Then I was able to see everything as root running Main Menu editor.
XFCE HAS TO MAKE THIS EASIER.

---

### Post by LewisTM on 2012-09-17
This is an old thread but I can still provide some useful information.
Indeed alacarte is not the ideal menu editor for XFCE. It misses a lot of entries and lacks the ability to specify advanced options.
**MenuLibre** fills that gap and is being considered as the main menu editor for Xubuntu 12.10.
Install it with 
```
sudo add-apt-repository ppa:menulibre-dev/devel
sudo apt-get update && sudo apt-get install menulibre
```
You can find the item in Xfce->System->Menu Editor.
MenuLibre has support for quicklists, multiple categories and has a built-in .desktop file editor. 
The main reason we sometimes can't find items is because of lines in the .desktop file like NotShowIn= or OnlyShowIn=Unity/XFCE/GNOME/etc. Edit those lines to your preference depending on your DE and usage.

Cheers!

---

### Post by doktorOblivion on 2012-09-17
I guess my point is that many entries are not modifiable by the logged in user's version of Main Menu.  Those things that have been installed using sudo apparently are owned by root and are not modifiable when the user simply clicks on the Main Menu item in Properties.  It would be nice if one could also gksudo that item so that it would ALWAYS run as root, therein removing the issue.  Is that possible and how/where would I make such a change?

---

### Post by LewisTM on 2012-09-17
I'm not sure what you mean. When a user runs alacarte (or menulibre) and modifies an entry, the editor reads from /usr/share/applications/yourapp.desktop and writes the modified entry as ~/.local/share/applications/yourapp.desktop

The modified user .desktop file overrides the system default in the menu. That's another nice feature of Menulibre, it shows you in the bottom right corner whether the launcher is a system or user entry and you can delete the user entry if you want to revert.

---

### Post by Buntu Bunny on 2012-09-19
> **LewisTM said:**
> 
**MenuLibre** fills that gap and is being considered as the main menu editor for Xubuntu 12.10.
Install it with 
```
sudo add-apt-repository ppa:menulibre-dev/devel
sudo apt-get update && sudo apt-get install menulibre
```
You can find the item in Xfce->System->Menu Editor.
MenuLibre has support for quicklists, multiple categories and has a built-in .desktop file editor. 


Well, I'm going to look into this. I am wanting to create submenus to organize things. I tried lxmed but it couldn't do that.

---

### Post by LewisTM on 2012-09-20
Well, MenuLibre is not perfect. It has a fixed set of categories and does not support submenus. Maybe a later version will. For now is use it as a superior launcher editor.

---

### Post by Buntu Bunny on 2012-09-20
> **LewisTM said:**
> Well, MenuLibre is not perfect. It has a fixed set of categories and does not support submenus. Maybe a later version will. For now is use it as a superior launcher editor.

That's what I was afraid of. :(  Thank you LewisTM, for that. Maybe I'm wishing for something that doesn't exist. ;)

---

### Post by Frogs Hair on 2012-09-20
Right click where is says Applications Menu to enter properties. Select edit menus from the center of the dialog box to open the main menu and then add or remove items.

---

### Post by Buntu Bunny on 2012-09-20
> **Frogs Hair said:**
> Right click where is says Applications Menu to enter properties. Select edit menus from the center of the dialog box to open the main menu and then add or remove items.

Thanks Frogs Hair. Yes, I found that too, and could create submenus, but I couldn't move any installed software into my new folders. I didn't mess around with it much after that.

---

### Post by Frogs Hair on 2012-09-20
I just created a new menu and a new item.

1. Selected  new menu from the main menu named it favorites(any name you want)
2. Selected no icon to get into the icon directory.
3. From the drop-down selected an icon category and chose an icon.
4. Select create.
5. Opened properties of the item I wanted to move to the new menu. (double click) 
6. copied and pasted the description, command, and comment to gedit. 
7. Selected my new favorites menu from the left pane of the main menu.
8.Selected new item .
9.pasted the information into my new launcher properties.
10.Selected no icon to get back into the icon directory and found an icon.
11. selected create from the properties dialog box. 

At this point you can delete the old launcher from the main menu where it was previously located.

---

### Post by Frogs Hair on 2012-09-20
This what I ended up with. The icon choices were not great because it was just for testing.

---

### Post by Buntu Bunny on 2012-09-20
Frogs Hair, I will give this a try tomorrow. Your steps look more detailed than what I tried. I'll let you know how it goes. Thanks!

---

### Post by Buntu Bunny on 2012-09-21
> **Frogs Hair said:**
> This what I ended up with. The icon choices were not great because it was just for testing.

Works for me! Also helping me resolve a problem I was having with adding a dock launcher. Many thanks!

---

### Post by Frogs Hair on 2012-09-21
Glad it worked , I'm using Dockbar x with XFCE and I have Unity and the Gnome shell also. I have been using XFCE for about five days. The last time I tried it I didn't give it enough time to learn it very well. ;)

---

### Post by Buntu Bunny on 2012-09-21
I have Unity and Gnome shell as well, but I really like Xfce the best. It may not be as smooth around the edges so to speak, but for me, it's a much more usable DE. Especially like how configurable it is. I hope you give it a fair shot. :)

---


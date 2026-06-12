---
title: "What's your favourite dock/themes"
date: 2011-03-17
forum: Desktop Environments
---

### Post by Poppyann on 2011-03-17
Hi everyone,

I installed Ubuntu again this morning, and Im just wondering what your favourite Docks and themes are! (I need some ideas ) 

ALSO: Your favourite Widget/desktop gadget software? I really liked the Kubuntu ones, are there some similar on Ubuntu?
 Thanks

---

### Post by dodo3773 on 2011-03-17
> **Poppyann said:**
> Hi everyone,

I installed Ubuntu again this morning, and Im just wondering what your favourite Docks and themes are! (I need some ideas ) 

ALSO: Your favourite Widget/desktop gadget software? I really liked the Kubuntu ones, are there some similar on Ubuntu?
 Thanks

The dock I use right now is cairo-dock. A lot of people seem to like docky though. Also, there is awn. As far as themes go I use Emerald for my window borders, conky for my "desktop gadget software", and  just regular gnome theme for the rest.

My set up now is

Controls Theme=slickness black
Icons=Voyager 2 Dark
Mouse=Aero Drop
Emerald=Not sure. It is a glassy theme. But I customised it and renamed it for backup purposes so many times that I do not remember.

Not sure if you were using kde-look, but there is a gnome-look website as well. I get all of my stuff there. You could spend a whole day just figuring out what you want (they have a lot of themes). Also, conky was a pain for me to figure out at first. But after I did I realised how great it is. Have fun.

---

### Post by Poppyann on 2011-03-17
> **dodo3773 said:**
> The dock I use right now is cairo-dock. A lot of people seem to like docky though. Also, there is awn. As far as themes go I use Emerald for my window borders, conky for my "desktop gadget software", and  just regular gnome theme for the rest.

My set up now is

Controls Theme=slickness black
Icons=Voyager 2 Dark
Mouse=Aero Drop
Emerald=Not sure. It is a glassy theme. But I customised it and renamed it for backup purposes so many times that I do not remember.

Not sure if you were using kde-look, but there is a gnome-look website as well. I get all of my stuff there. You could spend a whole day just figuring out what you want (they have a lot of themes). Also, conky was a pain for me to figure out at first. But after I did I realised how great it is. Have fun.

Thanks for you suggestions, your setup sounds good. 
I do like slickness black actually :)

---

### Post by Copper Bezel on 2011-03-17
For docks, I always have to pimp Avant Window Navigator. It's relatively simple to configure, comes with most of the gadgets from Gnome Panel, and can be anything from a dock to a panel (or both at the same time, since it can run multiple panels.)

+1 for Emerald. I don't use it personally, but it's a lot easier to get things looking prettier, faster, with Emerald over Metacity.

For themes in general, just take a look around Gnome-Look, as Poppyann suggested. There are plenty of GTK/Metacity, Emerald, icon, and X-cursor themes available for whatever look you want. Trending right now are the Faenza icons and the Elementary theme.

Edit: Incidentally, here's AWN being a dock and panel at the same time. = )

[http://ubuntuforums.org/showpost.php?p=10561301&postcount=290](http://ubuntuforums.org/showpost.php?p=10561301&postcount=290)

It's using the DockbarX plugin as well.

---

### Post by Poppyann on 2011-03-17
> **Copper Bezel said:**
> For docks, I always have to pimp Avant Window Navigator. It's relatively simple to configure, comes with most of the gadgets from Gnome Panel, and can be anything from a dock to a panel (or both at the same time, since it can run multiple panels.)

+1 for Emerald. I don't use it personally, but it's a lot easier to get things looking prettier, faster, with Emerald over Metacity.

For themes in general, just take a look around Gnome-Look, as Poppyann suggested. There are plenty of GTK/Metacity, Emerald, icon, and X-cursor themes available for whatever look you want. Trending right now are the Faenza icons and the Elementary theme.

Edit: Incidentally, here's AWN being a dock and panel at the same time. = )

[http://ubuntuforums.org/showpost.php?p=10561301&postcount=290](http://ubuntuforums.org/showpost.php?p=10561301&postcount=290)

It's using the DockbarX plugin as well.

I have AVN installed right now, with a nice theme. I also installed a decent icon theme too, I'm learning! Lol.

The panel & dock setup looks really good. I don't know how to add the panel icons such as volume, wifi tools etc to it though, I have the default panel on autohide which is working well.

---

### Post by false truths on 2011-03-17
I've been rocking AWN-trunk with DockBarX for a while now.

Also using the Orta theme with the Orta Emerald decorators, and Faenza icons.


As far as putting gnome-panel stuff in your dock, the notification area and indicator applet cover the majority of things, while the digital clock and quit-logout applets can be added to make a nice complete system/session panel.


As far as my AWN setup, I have a MintMenu applet added because I find it a lot more comfortable then any of the default AWN menus. My left dock is set to a small icon size, and it holds my MintMenu, File Browser Launcher, Tomboy Applet, Trash, and Show Desktop. My top dock is almost completely to the right. It holds my Quit-logout Applet, Digital Clock, Indicator Applet, and Notification Area. Both of these docks are set to Intellihide and Transparency, although since I'm not running the AWN taskmanager they just go auto transparent. My third and final dock is in the bottom center of the screen. This only holds one applet, the entire reason I choose AWN over Cairo: DockBarX.

---

### Post by Copper Bezel on 2011-03-17
If you want the docks to Intellihide but are using DockBarX instead of the Taskbar, you can go into the taskbar settings and remove all the launchers, then set it to "display only launchers". You can drop it into the dock and, without anything to display, it doesn't take up an icon slot, but it manages the Intellihide function.

Poppyann: One note on the indicator applet and notification area is that the notification area can only run in one place at a time, so you have to remove it from Gnome Panel before you can add it to AWN. If you want to ditch Gnome Panel completely, you'll need to go into gconf-editor (or Ubuntu Tweak) and change the panel key in /desktop/gnome/session/required_components to Avant-Window-Navigator so that Avant loads instead of the panel on startup.

---


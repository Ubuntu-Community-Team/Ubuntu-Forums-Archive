---
title: "Create Custom Categories"
date: 2013-10-30
forum: Desktop Environments
---

### Post by adec2 on 2013-10-30
Hi how can custom categories be created in ubuntu? I see when you install Wine it creates its own so it must be possible. I understand alacarte can do this but I would like to find out if there is another way to add for example "Commodore Amiga" category then add custom amde shortcuts to that folder without alacarte (main menu)
I am using Ubuntu 13.10 and alacarte is totally broken for making new categories now

---

### Post by vasa1 on 2013-10-30
> **adec2 said:**
> Hi how can custom categories be created in ubuntu? I see when you install Wine it creates its own so **it must be possible**. ...
Agreed. I had done it before. I seem to remember having to edit xml-format *.menu files in /etc/xdg. I guess the exact filename (and path) will depend on your desktop environment.

---

### Post by mc4man on 2013-10-31
What is your intended means of using this 'custom cat..'?
If it's thru a dock & quicklists, (unity, docky, plank),  then simply create a cat. .desktop with quicklist entries. The left click action can be any one of the related apps you wish or be made non functioning though can't see doing that.
(- the main .desktop of the dock icon is eligible for DnD on registered/listed mimetypes

As far as the Dash, if using, (I don't much for apps), I'd think it uses any app's actual .desktop & maybe some word(s)   in it for  searches

---

### Post by adec2 on 2013-10-31
At the moment I have categories like, "Accessories, System, Graphics, Sound & Video, Programming, Office, Internet" etc and any installed program is thrown into the appropriate category as stated in the "Categories=" in the .desktop file. What I would like to know is how these Categories are made, there must be a way to add them as A "Wine" catgory appears when you install Wine, not only that but alacarte is obviously able to add Categories (Unfortunately it seems broke in 13.10). I would like to know if it is possible for little me to add one easily or even if anyone has any knowledge on how Wine/Alacarte adds these custom Categories.
 Eventually what I want is to make a custom category for example with the name "Atari" so i can add all my custom made .desktop files into it, i like my games and prefer to have them in categories than all lumped into either the "Other" category or the "Games" category. I have way too many .desktop files to lump them into one category

---

### Post by adec2 on 2013-10-31
> **vasa1 said:**
> Agreed. I had done it before. I seem to remember having to edit xml-format *.menu files in /etc/xdg. I guess the exact filename (and path) will depend on your desktop environment.

 Interestingly I have a "Wine.menu" in the folder /etc/xdg/menus/applications-merged   with these contents

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
"http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">
<Menu>
  <Name>Applications</Name>
  <Menu>
    <Name>wine-wine</Name>
    <Directory>wine-wine.directory</Directory>
    <Include>
      <Category>Wine</Category>
    </Include>
  <Menu>
    <Name>wine-Programs</Name>
    <Directory>wine-Programs.directory</Directory>
    <Include>
        <Category>Wine-Programs</Category>
    </Include>
  <Menu>
    <Name>wine-Programs-Accessories</Name>
    <Directory>wine-Programs-Accessories.directory</Directory>
    <Include>
        <Category>Wine-Programs-Accessories</Category>
    </Include>
  </Menu>
  </Menu>
  </Menu>
</Menu>

and also points me to the html file located here, i wonder if this is it?

/usr/share/doc/menu/html/index.html

Also this page has some interesting information

[http://wiki.matusov.sk/howto/gnome-menu-edit](http://wiki.matusov.sk/howto/gnome-menu-edit)

---

### Post by adec2 on 2013-11-01
Ok i've managed to get this done. I will give a quick how to based on a new custom folder called "Atari 800" (That's the shortcuts i originally wanted seperate from the rest)

1..Create a file called atari800.menu (substitute atari 800 for whatever you want to call it) in the folder location etc/xdg/menus/applications-merged
2..Input these contents

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
"http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">
<Menu>
  <Name>Applications</Name>
 
  <Menu> <!-- atari800 -->
    <Name>atari800</Name>
    <Directory>atari800.directory</Directory>
    <Include>
      <Category>atari800</Category>
    </Include>
  </Menu> <!-- End atari800 -->
 
</Menu> <!-- End Applications -->

3..Save file and create another  file called "atari800.directory" in the folder location
 usr/share/desktop-directories  with these contents

[Desktop Entry]
Type=Directory
Name=Atari 800
Icon=/home/ade/Icons/atari800folder.png

**Note** the .directory name should be exactly the same as the .directory name you entered in the .menu file above (In my case atari800.directory NOT Atari 800.directory with a space.

4..Create a standard .desktop file in ~/.local/share/applications  with these contents (substituting for your own program of course and the Categories= line MUST BE the same as the name you gave the .directory file eariler, in my case atari800)

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=atari800 -fullscreen -bilinear-filter -artif 0 -vsync -pal -fit-screen height -image-aspect none "/media/Stuff/Roms/Atari800/Goonies, The (1985)(Datasoft)[cr NAPO][t].atr"
Name=Goonies
Icon=/home/ade/Icons/Atari800/atari-goonies_6_256x256x32.png
Categories=atari800
Comment=Atari 800


 Hope it helps people and the link above, in my previous post also gives a description on how to make sub menus as well

---


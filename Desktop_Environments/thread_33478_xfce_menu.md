---
title: "xfce menu"
date: 2005-05-11
forum: Desktop Environments
---

### Post by b3nw on 2005-05-11
Just moved to xfce today, enjoying it alot, but the menu is horrid, from what I've found, it is auto generated somehow.  ](*,) 

I was wondering if there was a way to open up via gedit or nano the menu.lst from xfce, and open up a similar file in gnome, and then I could just start copying info (not directly of course would have to change the format, but the icons/launch locations).

I found the xfce4 menu.lst easy, but the gnome one is no where to be found? Only able to find gui programs that edit it for you.

Thanks in advance,

---

### Post by defkewl on 2005-05-11
What do you want to do? I still don't get it :(

---

### Post by b3nw on 2005-05-11
the xfce menu is auto generated. (at least thats what the file says).

I don't want it to  be, but I want to be able to get a list of program names/icons from the gnome menu file.

Can't find the gnome menu file.
hope thats simpler...

---

### Post by emendelson on 2005-05-11
There is no Gnome menu file. The entries are put together dynamically from the *.desktop files in /usr/share/applications and ~/.local/share/applications and a few other places. 

I would switch to xfce in a moment if there were an easy way to edit the menu, but I haven't found one.

---

### Post by mrbass on 2005-05-11
To remove duplicate menu items just do this once (assuming you have kubuntu or kubuntu-desktop installed)
 sudo rm -rf /usr/share/apps/kappfinder/apps/

Now as far as adding a few apps just install the text entries in /usr/share/applications and it'll be picked up.  Just view other .desktop entries for examples.

Now as far as editing like menueditor in GNOME (guess you could use that one in XFCE4 perhaps..not sure)..but it is planned feature for next version after XFCE 4.2.1 ...maybe 4.4 I think.

---

### Post by darkaudit on 2005-05-11
[QUOTE=mrbass]To remove duplicate menu items just do this once (assuming you have kubuntu or kubuntu-desktop installed)
 sudo rm -rf /usr/share/apps/kappfinder/apps/
[/QUOTE]I did that, and all I lost were the apps in the 'Terminal' submenus. Since the Debian menu is still there, I really didn't lose anything. :)

---

### Post by b3nw on 2005-05-12
I found a menu editor, but its not user friendly  ](*,) 

Thanks for the info, it helped alot  O:)

---

### Post by tread on 2005-05-12
xfce comes with a menu editor, doesn't it?

---

### Post by mrbass on 2005-05-13
[QUOTE=darkaudit]I did that, and all I lost were the apps in the 'Terminal' submenus. Since the Debian menu is still there, I really didn't lose anything. :)[/QUOTE]

Only do that if you installed kubuntu-desktop (in other words if you have KDE installed along with XFCE4).

---

### Post by darkaudit on 2005-05-13
I've got hdd real estate to spare, so I've got GNOME, KDE, Blackbox, Fluxbox, and XFCE all installed. XFCE is the current favorite. :)

---


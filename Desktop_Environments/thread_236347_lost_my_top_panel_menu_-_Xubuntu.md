---
title: "lost my top panel menu - Xubuntu"
date: 2006-08-14
forum: Desktop Environments
---

### Post by maniacmusician on 2006-08-14
Hey,

I'm running Xubuntu 6.06...
my problem is that I have made my "Applications" menu in the top panel dissappear. Earlier, I was editing my menus, and I created a new menu file that I could add as a submenu to my existing one, and when saving, I think i overwrote ~/.config/xfce4/desktop/menu.xml. At first, nothing happened. I opened the menu editor again, and went to add my newly created menu as a submenu. Thinking that ~/.config/xfce4/desktop/menu.xml was just where I had saved my new file, I added that. At that point, things started to freeze up and menu editor went on the fritz. my top and bottom panels dissapeared and returned shortly, but with the "Applications" menu missing. I went to use the right click menu on the desktop, only to find that it wasn't there either. Someone suggested that I delete the existing menu.xml file, and when I logged back in, everything would be fixed. I took his advice. now i have my right click menu back, but still no Applications menu. Any help would be appreciated.

thanks.

edit: already tried a search and some of the suggestions on this forum, none worked except for the one that brought my right click  menu back.

---

### Post by maniacmusician on 2006-08-14
Hi;

I figured it out. For anyone else that maybe has this problem, all you have to do is go to the top panel, right click, add new item. Go down to the bottom, selec "XFCE Menu." Then for the title, you just say "Applications", and for the icon, you go to /usr/share/pixmaps and select "xubuntu-logo.png" i hope that helps someone.

---


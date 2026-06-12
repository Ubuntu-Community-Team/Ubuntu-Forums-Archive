---
title: "Why is everything dissapearing?"
date: 2005-04-03
forum: Desktop Environments
---

### Post by h4n9m4n on 2005-04-03
well, i love gnome and all, but i wish the menus were like KDE. So far in gnome, everytime something is added to the menu, it eaither disappears the next time i log on or reboot. Ive installed crossover, and i used to have a folder for it on my apps menu. When i logged off and back on, it was gone. So far the only thing that has stayed is my transgaming menu. and that only has the link for point2play, and not the games themself. does anybody know a solution?

---

### Post by valadil on 2005-04-04
I think the problem is with Debian (which ubuntu is based on) and not with gnome.  Debian has this little program which goes by the name of menu.  If you set up your menus using Debian's menu, in theory menus will be updated when you apt-get install programs.  Additionally when you get a new window manager the debian menu script will translate your menus into the new wm.  It's actually pretty cool and kinda useful.  It just sucks that the only way to discover this feature involves losing your menus once or twice.

---

### Post by h4n9m4n on 2005-04-04
what should i do then?

---

### Post by heruwdp on 2005-04-04
i am using menu, for updating my menu after i installed a software

 $sudo apt-get install menu

for updating

 $sudo update-menus

hope this help :)

---

### Post by bored2k on 2005-04-04
Add 
sudo apt-get install menu-xdg [with the above by heruwdp]

---

### Post by h4n9m4n on 2005-04-05
um, all
sudo update-menus
did was create a debian entry in my applications menu. The debian entry contains exactly what my gnome menu contains.. so i have my menu inside my menu.  :?: 
no crossover menu, no windows applications menu. any help will be appreciated... i just want all my menu icons to show, thats all...

---

### Post by kiddo on 2005-04-05
Hadn't done any of the above, but I'm still stuck with that uncool "debian" self-inclusive menu. How to get rid of it? Boy I'm eager to have that Gnome 3.0 menu editor.

---

### Post by h4n9m4n on 2005-04-05
ah, i think im just gonna make the switch to kubuntu. i love gnome's look, but kde handles icons better, and i need my shortcuts. but if someone finds a solution to this problem, post! i'd like to know.

---


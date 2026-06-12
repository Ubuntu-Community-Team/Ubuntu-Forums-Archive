---
title: "Menu and Folder Icons Absent"
date: 2013-10-17
forum: Desktop Environments
---

### Post by QuestVicious on 2013-10-17
First off any help given is greatly appreciated. 

I'm running Ubuntu 12.04 LTS Cinnamon Remix. Now system works fine and is very stable, but my normal folder and menu icons disappeared after I installed routine updates that came up on the update manager. 

Here's what I'm looking at:

Menu
[[IMG]http://s23.postimg.org/m8cpxm5l3/Menu_50.jpg[/IMG]]("http://postimg.org/image/m8cpxm5l3/")

Folders
[[IMG]http://s11.postimg.org/o0ayz4qq7/folders.jpg[/IMG]]("http://postimg.org/image/o0ayz4qq7/")


I'm been giving some thought to simply doing a re-install but I'm looking to fix this issue without having to do so. 

Thanks.

---

### Post by Stefan_Sinnige on 2013-10-20
I have the exact problem after doing an update through the update manager, on both of my machines. Everything seems to be working OK though, its just that the icons are no longer displayed (many of the application icons are OK though). During this update, cinnamon was updated from 1.8 to 2.0.

---

### Post by kill_io on 2013-10-21
also same here. using ubuntu 12.04.3 64bit and nvidia graphics. also updated using the update-manager.

i'd also like to avoid a reinstall. maybe i'll give cinnamon a reinstall try...

ps: additionally i cannot select any category (office, internet, graphics etc) in the main menu. the right list with the actual programs works fine.

---

### Post by Stefan_Sinnige on 2013-10-21
I solved it now. It appears that it defaults to the gnome icon theme, which might be broken !?!  Whenever I run "cinnamon-settings themes" in a terminal and go to the "Other Settings" tab, I can change the 'Icons' to a different theme. The 'ubuntu-mono-light' seem nice. You may need to logout/login for the whole menu to be updated.

---

### Post by kill_io on 2013-10-22
awesome! thx a lot. worked here too.

---


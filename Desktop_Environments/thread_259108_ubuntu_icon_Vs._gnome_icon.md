---
title: "ubuntu icon Vs. gnome icon"
date: 2006-09-16
forum: Desktop Environments
---

### Post by bluefuse on 2006-09-16
I know there is a way on ubuntu 5.10 to get the gnome icons back on the taskbar, but I cannot find a way to restore the gnome icons on 6.0.6, does anyone have any suggestions?:-\"

---

### Post by wargames on 2006-09-17
Is this what your looking for?

[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

Hope this helps. :D

---

### Post by bluefuse on 2006-09-17
rm: cannot remove `/usr/share/icons/hicolor/48x48/apps/distributor-logo.png': No such file or directory



um.......not sure what wrong with this......

---

### Post by bluefuse on 2006-09-17
ok I looked in the directory and that ubuntu icon is not there....but gnome is......hmmm

---

### Post by arkangel on 2006-09-17
on top of this directory  there is a file like icon.cache or soemthing  just remove that file

---

### Post by bluefuse on 2006-09-17
ok problem, I went back into that directory, I see no cache file, nor a gnome file nor a distributor file......

---

### Post by bluefuse on 2006-09-17
ok I found that file but as a sudo or regular user account I cannot delete it, and I dont know how to do this per terminal.....
](*,)

---

### Post by arkangel on 2006-09-17
open a terminal  and type
# cd  /usr/share/icons/hicolor/  
# sudo mv icon-theme.cache  icon-theme.cache.bk

then  remove the menu from the panel  and add it again , to do this  right click  on the panel and "add to panel"


EDIT: it should work , if not , change the name of the icon you want to use   to distributor-logo.png
so terminal and type 
# cd   /usr/share/icons/hicolor/48x48/apps/
# mv  [myiconname].png  distributor-logo.png  
and try again

---

### Post by bluefuse on 2006-09-18
going round and round with this issue, I did everything I can think of, I removed it, I removed the cache, I rebooted and added the panel, I verified from the begining, that the icon distributor-logo.png was not in the directory in which was specified.....user/share/icons/hicolor/48x48 now, the gnome icon is there so I think that its very possible the the dristrubutor icon path is different. I dunno I am stunned, I dont know what to do at this point.

---

### Post by patrickfromspain on 2006-09-18
I'm using a custom icon theme (icons from various different themes) and, in one folder, I place the gnome-foot. THe file is called start-here.png and there are 3 files symlinked to it (distributor-logo.png, gnome-main-menu.png and novel-button.png). So, when I choose the Human icon theme, I get the ubuntu logo, and with my theme I get the gnome-foot. 

Anyway, in the human theme, you'll find those 4 files under /usr/share/icons/Human/48x48/places

Hope it helps :)

---

### Post by bluefuse on 2006-09-18
I was getting ready to post that very same bit of infor, I found it scrolling around trying to find the trash can icon for my desktop shortcut.

good find

---

### Post by bluefuse on 2006-09-18
patrick from spain, I tried something like what you had suggested, but I am stumped, the icon to add the menu to the taskbar is the correct icon, but when I add it to the bar, then old ugly ubuntu shows its face...

sudo mv /home/yourusername/distributor-logo.png usr/share/icons/Human/48x48/places 
sudo mv /home/yourusername/gnome-main-menu.png /usr/share/icons/Human/48x48/places 
sudo mv /home/yourusername/start-here.png /usr/share/icons/Human/48x48/places    

](*,)

---

### Post by bluefuse on 2006-09-18
This is based on the same technique used to get the gnome foot back in Breezy. For Dapper, it's a little trickier but here goes:

First get the gnome-menu-logo.png no save it as 3 different files, you will want to renmae these files first thing (start here.png,gnome-main-menu.png,distributor-logo.png) store all three files in you home folder, proceed to the next step, open up at teminal and enter in the following; 

sudo mv /home/yourusername/distributor-logo.png /usr/share/icons/Human/48x48/places
sudo mv /home/yourusername/gnome-main-menu.png /usr/share/icons/Human/48x48/places
sudo mv /home/yourusername/start-here.png /usr/share/icons/Human/48x48/places sudo /usr/share/icons/Human/index.theme /home/yourusername

Then delete the file from your home folder and remove the menu bar and reboot your pc, the add the menu bar back, you should see the new icon in the add/remove.

With any luck, the classic Gnome foot will be back. 

The following site has been updated on 6.0.6 [http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

---

### Post by arkangel on 2006-09-19
I didnt  realize i am using another icon theme ,  the ubuntu icon in the  human icon theme is die-hard,  
try to change to another theme and the icon will be what you have specified (the gnome defualt or something else instead of the  ubuntu-logo )   if you still are not able to change  i will paly around  i will post if i succeed

---


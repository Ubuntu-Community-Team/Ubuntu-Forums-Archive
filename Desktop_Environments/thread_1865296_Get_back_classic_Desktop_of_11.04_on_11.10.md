---
title: "Get back classic Desktop of 11.04 on 11.10"
date: 2011-10-19
forum: Desktop Environments
---

### Post by razorxpress on 2011-10-19
Some of you might want to get the old classic look back. It is not 100% as it was in 11.04 classic but with these settings you get most of them back.

In this article I will configure ubuntu 11.10 to get class window back. It will have main menu instead of menubar. 
1. Install gnome-panel
 
$ sudo apt-get install gnome-panel

Source :[http://www.addictivetips.com/ubuntu-linux-tips/get-classic-start-menu-in-ubuntu-11-10-oneiric-ocelot/](http://www.addictivetips.com/ubuntu-linux-tips/get-classic-start-menu-in-ubuntu-11-10-oneiric-ocelot/)

2. Login to "Gnome Classic" from login screen

3. Delete bottom panel
Use Alt + Right Click and delete it.

4. Bring top panel to bottom
Use Alt + Right Click, go to properties and set Orientation to Bottom. Change the size to 22. Select Properties -> Background make it opaque and choose color value to #3F3E39. I did not get even color around notification icons and date, when I tried to use panel image as background, so this color choice is a better option.

Source: [http://www.blog.poggs.com/2011/10/ubuntu-11-10-for-productive-people/](http://www.blog.poggs.com/2011/10/ubuntu-11-10-for-productive-people/)

5. Get back icons.
Using Alt + Right Click delete unnecessary icons. The one that causes the panel to look big is Use Menu (so don't use it). Get Main Menu, Show Desktop, Logout, Shutdown, Notification Area and Clock. Using Application Launcher get terminal, firefox. Using Custom Application Launcher create a launcher for your home directory (command is nautilus /home/yourusername, give it an icon using /usr/share/icons/ubuntu-mono-dark/places/48/folder-home.svg).

6. Delete global menu
$ sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt

To get the global menu back (if you choose to use unity for change)
sudo apt-get install appmenu-gtk3 appmenu-gtk appmenu-qt

Note: Keep these scripts handy. Or for ease create a script that does this and execute them whenever needed.

Source: [http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-global-menu-in-ubuntu-11-10-tip/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-global-menu-in-ubuntu-11-10-tip/)

7. Align window button to right

$ gconftool-2 --set /apps/metacity/general/button_layout \
 --type string "menu:minimize,maximize,close"
 
Note: If you don't like menu then you can use just ":minimize,maximize,close"

Source: [http://askubuntu.com/questions/66541/align-window-buttons-to-the-right-in-gnome-fallback-mode](http://askubuntu.com/questions/66541/align-window-buttons-to-the-right-in-gnome-fallback-mode)

8. Adding the compiz fun back.
There is a nuisance though. If you start compiz you will not be able to add icons to you panel unless you disable it again. Go to Other-> Startup Applications and Add an entry. Give any name you want, but in Command  put "compiz --replace" without quotes. Next start CompizConfig Settings Manager (ccsm) and disable unity. Go to Window Management and check if Application Switcher, Grid, Move Window, Place Windows, Resize Windows, Scale are checked. Change others as you prefer. When you logout and login you have your compiz working. If you want to add icons to your panel you can disable compiz from Startup Applications logout and login to add icons and re-enable it after you are done.

If something goes wrong and you could not log out. Command to reset would be

$ sudo service lightdm restart

9. Conclusion
Thats all. If there are other things that can be improved please include.

See the [screen-shot]("http://ubuntuforums.org/attachment.php?attachmentid=204905&stc=1&d=1319082190").

---

### Post by kwanylongy on 2011-11-06
Excellent! This is exactly what I need! Thanks!

Carlos

---

### Post by Clancy_s on 2011-11-22
Hooray! Many thanks.

---

### Post by ssdt on 2012-02-16
Thanks a lot. Because of the new ubuntu unity desktop, i had changed to linux mint. now i will be changing back to ubuntu.

ubuntu dev should totally get back the old desktop and make the unity an addition that people could switch to

---

### Post by Bucky Ball on 2012-02-16
You can also make Xfce pretty similar with some tweaks.

---


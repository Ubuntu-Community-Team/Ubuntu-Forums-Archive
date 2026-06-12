---
title: "How get a Gnome like panel for Xfce"
date: 2010-12-21
forum: Desktop Environments
---

### Post by kliffs on 2010-12-21
Hello, 
I have been running ubuntu 10.10 on a old laptop for a while but have started to get tired of the high resource usage. I installed xfce via xubuntu-desktop package and all worked well but the menu. It is the Xfce menu not the customized xubuntu panel and i really dont much like it. Is there a way to fix this? any help is appreciated.

---

### Post by hhh on 2010-12-22
You have given no specifics, what is it about Xfce's menu that you don't like, or what is it about Gnome's that you do? That being said, the Xfce menu is very clumsy to edit right now, you have to do it manually. This will be changed in the new version due out next month.

Removing menu items is easy enough, though. Open Thunar as root in the Run dialog (Alt+F2, then run "gksu thunar" without the quotes). Navigate to /usr/share/applications. Careful, the icons represent .desktop files and are very weird to work with, for example renaming one can cause it to disappear. Anyway, say you want to remove "Application Finder" from the Accessories menu... right click that icon and open it with Mousepad. Now scroll to the bottom and add the line "NoDisplay=true" and save the file. Instantly the menu entry will be gone.

---

### Post by kliffs on 2010-12-23
Thanks for getting back to me so fast.

It turns out I am having many more problems than I thought. Every time I log on the panels need to be rearranged, I cant move files to the trash wich sucks because due to some impulsive partitioning i dont have enough room to download a new cd image to install a working OS or boot a GParted for repartitioning. On top of all this it won't even shut down. I have to manually hold the button until it cold turns it self off. I have an old liveCD from ubuntu 10.04 that i would use but the computer shuts off during boot. It took me hours to get networking working so i could even come here for help. I'm wondering if using the same /home partition as my last install is what is causing this. I stumbled across a Xubuntu 10.10 image on another partition which i manually mounted and moved files around so i could burn the image to a CD. If this doesn't work i am going to toss it out the window.

As for the original issue it was because the places menu wasn't there and the font was very small. I thought there might be a way to get a menu like Ubuntu with the system tab too. That is something i will work on after I actually have a working computer again.

I am new to Xfce and I hope I learn before I break something;) Thanks for trying to help anyway.

---

### Post by hhh on 2010-12-23
I think Xfce is the bomb. Try one of these distros if you decide to do a fresh install...
[http://debian.tu-bs.de/project/aptosid/release/](http://debian.tu-bs.de/project/aptosid/release/)
[http://www.pclinuxos.com/?page_id=213](http://www.pclinuxos.com/?page_id=213)
[http://en.opensuse.org/Xfce](http://en.opensuse.org/Xfce)

My aptosid desktop...

[[img]http://img820.imageshack.us/img820/5043/screenshot1218201010150.th.png[/img]](http://img820.imageshack.us/img820/5043/screenshot1218201010150.png)

---

### Post by bobcollard on 2010-12-24
Using your old Home in a separate partition is your main problem, the hidden files there are for your older version.  Backup your home files visible, Documents, music, pictures etc.  Then reinstall.  Suggest you try a Dock if the menu bothers you so much.  Cairo-dock is my favorite, there are many others that work.

---


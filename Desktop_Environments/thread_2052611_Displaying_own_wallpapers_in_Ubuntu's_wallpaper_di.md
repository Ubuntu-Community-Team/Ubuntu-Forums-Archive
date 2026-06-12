---
title: "Displaying own wallpapers in Ubuntu's wallpaper display"
date: 2012-09-03
forum: Desktop Environments
---

### Post by Philip Gray on 2012-09-03
Good evening

I am using Gnome Classic in 12.04.

I have been searching all the forums for away to get 12.04LTS to display my own wallpapers, which I have added to the 'usr/share/backgrounds' folder, and all the suggestions have not worked. 

I eventually discovered that 12.04 reads its' wallpaper information from the 'precise-wallpapers.xml' file which is located in 'usr/share/gnome-backgrounds-properties' folder. So I added my wallpapers to it. My problem/issue is that when I right click my desktop and select 'Change background' that except for my last four entries in the xml file I have two thumbnails for each wallpaper I added.

If I remove all my entries all the thumbnails disappear. Does anyone know why 12.04 would display two thumbnails for each single entry in the xml file? Very odd.

By the way I also installed the extra wallpapers available in synaptic and found that it installed some that were already there, and made duplicate entries in the xml file.

Regards
Philip

---

### Post by deadflowr on 2012-09-03
If you browse to file folder /usr/share/gnome-background-properties, select crtl+h to view hidden files. You will notice the precise-wallpapers.xml has a backup file. This file is also being read. Simply sudo rm the file from the terminal and you should have only one entry for wallpapers instead of two. Remember that the next time you add/save that file the same thing will happen.

You could also move the file to another place, like somewhere inside your home directory. That way when an update comes along and overwrites the existing file(which can happen from time to time) simply move your existing backup to replace the new file.

I learned about the backup xml file when I did the same thing, and a newer xml file came in and none of my additions were listed, but  all of my wallpapers were available in the wallpaper section of appearance.

It is definitely interesting how it works like that.

---

### Post by Philip Gray on 2012-09-05
Hi deadflwr

Thanks for yr help, it worked.

Regards
Philip

---


---
title: "changing icons in xfce"
date: 2008-01-26
forum: Desktop Environments
---

### Post by rolypolycat on 2008-01-26
Hello!
 I downloaded some nifty icons for linux in general, but there's no way to change the default icons in feisty xfce. When I right-click on the folder, it just shows basic info, and that's it. I can't click on the icon to change it. How can I use the new icons instead of the default xfce icons. And it's not just for the desktop; I want to change icons for file folders and whatnot, too. Any help is greatly appreciated.
Thanks!

---

### Post by MasterJS on 2008-01-26
Your going to need to create a folder in your home folder specifically for icons, and if later on you want themes your gonna have to make one for themes. Go to the terminal and type 
```
sudo mkdir /home/YOURUSERNAME/.icons
```
Basically what this does is create a directory (mkdir means make directory).
Now what you do is extract the tar.gz or whatever type of compression the file you downloaded it via the Archive Manager into the folder **.icons** (yes there is a period before icons).
Then what you do is go to XFCE MENU > SETTINGS > USER INTERFACE > PREFERENCES and then select the Icon Theme tab. Once your there, find the name of the icon set you download and apply. Thats all there is to it.
Now, if later on you want a new theme, all you have to do is make a directory called **.themes** (yes another period before the themes) and extract the themes into there and do the rest of the things i told you for the icons.

---


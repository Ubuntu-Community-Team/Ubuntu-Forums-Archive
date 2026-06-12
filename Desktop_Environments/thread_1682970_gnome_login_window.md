---
title: "gnome login window"
date: 2011-02-06
forum: Desktop Environments
---

### Post by computerfreak4284 on 2011-02-06
Hi I am trying to install a new gnome login window theme but for some reason I can not find login window under administration. I did install gdm from the package manager but it still does not show up.

---

### Post by andymorton on 2011-02-06
> **computerfreak4284 said:**
> Hi I am trying to install a new gnome login window theme but for some reason I can not find login window under administration. I did install gdm from the package manager but it still does not show up.

Unfortunately, since version 9.10 we can't install log in themes. The only way it can be configured is by manually changing the background etc. 

Have a look at this link to see how to do it. 

[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

andy :)

---

### Post by Copper Bezel on 2011-02-06
Actually, while it's true that the login screen theme can't be changed through apps that come with Ubuntu, it *can* be altered in-GUI. Use [UbuntuTweak]("http://ubuntu-tweak.com/").

---

### Post by JOHNNYG713 on 2011-02-06
Python GDM2 Setup [http://launchpad.net/gdm2setup/0.2/0.5.0/+download/python-gdm2setup.deb](http://launchpad.net/gdm2setup/0.2/0.5.0/+download/python-gdm2setup.deb)

Note: if you have installed any new themes, To get them to show in Python GDM2 Setup.
Open terminal type
```
gksudo nautilus
```enter your password
navigate system>home>yourname, 
Then press Cntl+h, This will open  hidden folders, Copy the contents of **.themes** to file  system>usr>share>**themes**, then go back to your home "unhidden  folders" and delete the themes in .themes ( or you will have two  instances show up in appearances menu of themes/icons ), do the same for  .icons, place the content of **.icons**  files from your unhidden home  folder .**icons,** To system>usr>share>**icons** then back to unhidden  home  folder> .icons and delete the content in .icons folder. ALSO when you copy themes and icons, While the folders are still Grayed out, Right click any Gray folder, click properties, click permissions tab, and set "Groups" and "Others" to "Access files" !
Python GDM2 Setup can be found in System Administration after install !

---

### Post by Copper Bezel on 2011-02-07
Even better! Cool!

---


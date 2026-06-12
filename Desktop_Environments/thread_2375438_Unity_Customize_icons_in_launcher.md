---
title: "Unity: Customize icons in launcher"
date: 2017-10-24
forum: Desktop Environments
---

### Post by mmvk on 2017-10-24
hi,
I am using Ubuntu 16.04 64bit with Unity. Is it possible to customize the icons in the laucher? In Gnome i can do that.
Best regards from Vienna
Yours
Manfred

---

### Post by Frogs Hair on 2017-10-24
Do you mean altering the default icon sets or installing 3rd party icon sets ?

---

### Post by mmvk on 2017-10-24
hi, thanks for the answer.
I would say that I want to alter the default icon sets AND install 3rd party icon sets.
In other words:
I have painted lots of icons in *.png and *.ico format.
In Gnome it is a standad so set your own icons.
Best regards sent from Vienna
by Manfred

---

### Post by Frogs Hair on 2017-10-24
In gnome you can use the main menu if installed to add your own icons. In unity, you could do this by opening the file manager with elevated permissions, navigate to usr/share/applications.

Next, find the icon you want to change, right click the icon to enter properties, select the icon image in the properties box and navigate to the folder with the desired image, select the image and select OK. This is easier than attempting to edit/ change the icon sets.

To see the change you may have to remove the applications from the launcher and pin them again. Always be careful in the file system and _one icon to definitely leave as is would be the file manger._

---

### Post by ajgreeny on 2017-10-24
If you're feeling really adventurous and like to use the cli, you should be able to use your own icons by editing the .desktop files for the applications you want to change.

You will have to do it as root but as the .desktop files are simply text files it is simple to list them first with ```
ls /usr/share/applications
``` which will give you the proper file name, not the launcher name which I believe is what shows in the file manager (nautilus).

You can then backup and edit the files you want with one command ```
sudo nano -B *name*.desktop
``` and change the Icon= line to show the full path to your own icon.

---

### Post by mmvk on 2017-10-24
hi,
I have found a way:

Terminal: sudo nautilus

In Nautilus:
/usr/share/applications.
Here are the icons which have been suggested by Unity.
Right hand click, properties, property-window. On left hand top is the icon proposed by Unity.
Left hand click on this icon, set YOUR icon, ...
The new icon in the launcher will be set after restarting the system.
Best regards from Vienna sent by
Manfred
PS: I cannot find the "solved"-button

---

### Post by deadflowr on 2017-10-24
Better option is to copy the .desktop file(s) from the /usr/share/applications folder into the user's ~/.local/share/applications folder.
You do this because files in /usr/share/applications will get overwritten on update, whereas the files in the user's home folder will not.
It also allows editing without root.
(well it can all be done without root, since you can copy from system folders into your home folder without root; note the opposite is not true, though)

You can also apply immediately by unlocking the launcher and then re-adding it.

The difference is that the files in the home folder will show up as filename.desktop files and so the icon might not appear; like it does in /usr/share/applications, but the icon will appear in the launcher.

> PS: I cannot find the "solved"-button

Go to Thread Tools at the right side above the first post, click on it and select
Mark this Thread as Solved

---

### Post by meetdilip on 2017-10-25
There are a few icon sets which you can use across most DEs. Numix, Paper and so on. The best way to use your own icons is to use one of these icon sets and modify the icon in it to the one of your choice

---

### Post by ajgreeny on 2017-10-25
And by the way, **YOU SHOULD NEVER use *sudo nautilus***.

The use of sudo is for command line applications only; using it on certain GUI applications can change ownership of files in your home to root and stop you logging in as user.
See RootSudo in my signature for more info.

---


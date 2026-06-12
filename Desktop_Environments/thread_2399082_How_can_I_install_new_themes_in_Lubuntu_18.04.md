---
title: "How can I install new themes in Lubuntu 18.04?"
date: 2018-08-21
forum: Desktop Environments
---

### Post by josefranw on 2018-08-21
Hello, my dear friends.

I have downloaded some theme packages from [https://www.opendesktop.org/p/1254680#files-panel](https://www.opendesktop.org/p/1254680#files-panel) and tried to install them using the steps described in [https://www.omgubuntu.co.uk/2018/08/new-gtk-themes-for-ubuntu-linux](https://www.omgubuntu.co.uk/2018/08/new-gtk-themes-for-ubuntu-linux) which are:


[LIST]
[*]Download one of the themes below
[*]Extract the archive to the ~/.themes/ directory in your Home folder
[*]Change GTK theme using the GNOME Tweaks tool
[/LIST]

But there is no .themes folder in my home directory.

How can themes be installed in Lubuntu if even possible?

Thanks.

---

### Post by Dennis N on 2018-08-21
You would need to create the **~/.themes** folder if it does not exist. This location is only good for the user owning the folder. Optionally, if you want the theme to be universally accessible by other users as well (including root), put the theme folder in **/usr/share/themes** 

Gnome Tweaks is not for Lubuntu. Instead,

**Menu > Preferences > Customized Look and Feel** opens the dialog to choose themes. 

Widget tab = select application theme (the kind you are installing) and then use "Apply" button.
 
Note: You can also install a different **icon theme**, **cursor theme** and **window border** theme if you want.

---

### Post by josefranw on 2018-08-21
Thank you for your answer. It worked.

---


---
title: "Larger Mouse Icon"
date: 2012-05-28
forum: Desktop Environments
---

### Post by CWM84 on 2012-05-28
Hello,

I am using Ubuntu 12.04.. Gnome.. I am wondering how do I make the mouse pointer bigger?? My mother needs it bigger to see better :)

Thanks,
Christopher

---

### Post by Frogs Hair on 2012-05-28
This link may help. [http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size](http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size)

---

### Post by CWM84 on 2012-05-28
> **Frogs Hair said:**
> This link may help. [http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size](http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size)

didnt work :(

put it on 36.. still the same size even after reboot... 

It was already on TMZ WHITE..

---

### Post by Dennis N on 2012-05-29
First you need to find a cursor theme that contains larger cursors. Look at gnome-look.org, category X11 mouse themes.

One such cursor theme: Flatbed Cursors which has 5 colors and 4 sizes.

Download the cursor package (archive), extract the folder of the cursor you want to use from the archive, and then copy or move that folder into /usr/share/icons

Then follow this post:

[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

You need to create the 2-line file named **cursor.theme** if it is missing from inside the cursor's folder, and save it there:

```
[Icon Theme]
Inherits=CursorName
```

Replace CursorName with the exact name on the cursor's folder. Case Sensitive. For example, FlatbedCursors.Blue.Huge

---

### Post by dodgeman4life on 2012-11-24
i am trying to do the same thing but when i copy my cursors to the icons folder it give me a error and says permission denied. how do i fix that?

---

### Post by Dennis N on 2012-11-25
> **dodgeman4life said:**
> i am trying to do the same thing but when i copy my cursors to the icons folder it give me a error and says permission denied. how do i fix that?

You need to start with sudo to give yourself temporary root privileges.

Start terminal and navigate to the location of the extracted theme's folder, then:

```
sudo cp -r theme-folder-name /usr/share/icons
```

'theme-folder-name' is the exact name of the theme folder you are copying.

---


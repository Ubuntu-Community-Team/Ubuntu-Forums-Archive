---
title: "Can't change gnome-panel launcher icons."
date: 2006-05-05
forum: Desktop Environments
---

### Post by red_Marvin on 2006-05-05
Well I have designed my own icon set for the program launchers on the gnome-panel.
But when I try to change it to the new file, they are all greyed out.
I have tried the changing following without success:
[LIST]
[*]file ownership
[*]file permissions
[*]file location
[*]filetype (both png and svg are AOK under other circumstances)
[*]file compression for png
[/LIST]

What am I missing?

---

### Post by Sutekh on 2006-05-05
When you change the Custom Icon and you browse to the folder that has your icon, you are actually browsing for the *folder* not the icon.


 - When you originally try to change the icon it opens a dialog box with the contents of /usr/share/pixmaps/ displayed.

 - Click browse and go to the icon folder you want (/usr/share/icons) and click **Open**.

 - Then it should go back to the first dialog box. Just press **Enter** to update the path and it should display the contents of your icon folder. 

 -  Alternatively just type the full path of the icons folder in the dialog box.


Check out this post by [audax321]("http://www.ubuntuforums.org/member.php?u=11439") for a fuller explanation with pictures.  [Ubuntu Forums - Access to Icons]("http://www.ubuntuforums.org/showpost.php?p=490790&postcount=4")

---

### Post by red_Marvin on 2006-05-06
It worked. Thanks!:D

---


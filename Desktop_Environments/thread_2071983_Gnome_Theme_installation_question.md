---
title: "Gnome Theme installation question"
date: 2012-10-16
forum: Desktop Environments
---

### Post by Deucalion29710 on 2012-10-16
OK so thanks to the people here at ubuntu forums I now have the capability to change my Gnome shell user themes.  I found one that I would like to install here:

[http://gnome-look.org/content/show.php/Prophet-3.6+Theme?content=153927](http://gnome-look.org/content/show.php/Prophet-3.6+Theme?content=153927)

I was able to decompress the file, but when I try to change to this theme using advanced settings there does not appear to be a select-able file in the folder.  If memory serves, and correct me if I am wrong, there should be a "themes" folder somewhere to move the extracted theme folder to.  Am I on the right track?  What is the path to the themes and icons folders?

---

### Post by Frogs Hair on 2012-10-16
You can install themes in one of two places. 
file system usr/share/themes. ```
gksu thunar
```

You can also create .themes folder in home. Use Ctrl + H to show hidden folders and create folder. If using 12.04 make sure themes are GTK 3.4 compatible. Prophet is a 3.6 theme.

Commands will vary with Thunar !

---

### Post by Deucalion29710 on 2012-10-16
Thank you very much!!!

---


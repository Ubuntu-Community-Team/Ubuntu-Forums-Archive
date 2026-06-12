---
title: "Gnome-Look Cursor Theme"
date: 2012-06-07
forum: Desktop Environments
---

### Post by DeltaFee on 2012-06-07
Hey,
   So I downloaded a cursor theme from Gnome look and I am confused on how to install it on ubuntu 12.04. I am using gnome-classic and I already have download gnome-tweak tool, but it does not give any options to add a new cursor theme. THxs

---

### Post by Enigmapond on 2012-06-07
Just extract to /user/share/icons or in the .icons folder in your ~/home

---

### Post by AbhiKap on 2012-07-10
Is there a way to open up the place to extract it using the terminal. or else how to get there?

---

### Post by stinkeye on 2012-07-11
Enigmapond had a typo.
/**usr**/share/icons not /**user**/share/icons

In the terminal open the directory as root...
```
gksudo nautilus /usr/share/icons
```

Then open another instance of the file browser as you would normally to your downloaded theme and drag and drop
your **extracted** theme folder to the root window you opened with **gksudo nautilus /usr/share/icons**

There is a bit more to making cursor themes work properly.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11929215&postcount=17")

---


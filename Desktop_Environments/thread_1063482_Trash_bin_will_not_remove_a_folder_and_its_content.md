---
title: "Trash bin will not remove a folder and its contents"
date: 2009-02-07
forum: Desktop Environments
---

### Post by xtiano77 on 2009-02-07
I plugged a portable hard drive to my machine and deleted a folder from there.  Everything went well during the deletion process; however, when I try to empty the Trash Bin, it will run through the motions, but the folder and its contents remain in the bin and the icon shows as if the bin was full.  Assuming that this is a glitch or bug, how can I overcome this?  Thanks in advance for your help.

---

### Post by Shazaam on 2009-02-08
Two places for trash...
1. /home/YOURUSERNAME/local/share/trash/files (and /info)
2. /root/local/share/trash/files (and /info)
Open terminal and enter this...
```
gksudo nautilus
```
This opens the nautilus file manager as ROOT so be careful. Find /home/local/share/trash and delete from inside the two folders there. When you go into the root/local/share/trash folders to delete the offending files inside highlight the files, hold down the SHIFT key and then hit your DELETE key. If you just right-click/delete them they will reappear.

---

### Post by xtiano77 on 2009-02-08
I opened the terminal screen and typed "gksudo nautilus"; however, when the Nautilus file manager open, I try following the path you specified, "/home/local/share/trash", but when I click on "home",all I see is my main folder and nothing with "/local/share/trash". I tried clicking on the "root" folder, but all it shows is the "desktop".

---

### Post by Vryko Lakas on 2009-02-08
> **xtiano77 said:**
> I opened the terminal screen and typed "gksudo nautilus"; however, when the Nautilus file manager open, I try following the path you specified, "/home/local/share/trash", but when I click on "home",all I see is my main folder and nothing with "/local/share/trash". I tried clicking on the "root" folder, but all it shows is the "desktop".
When you're in the Nautilus window, you might need to go up to View and tick the box next to "Show Hidden Files." This will give you a lot of previously-invisible folders with a "." before the name. One of these should be a .Local folder. Inside that is your Share folder, and inside *that* one is Trash. 
Within the Trash folder are two other folders, "files" and "info." I believe these are the two folders Shazaam wants you to get rid of.

---

### Post by xtiano77 on 2009-02-08
It worked like a charm. Thanks a bunch! I'll keep a copy of this instructions for future reference.  Thanks again!

---

### Post by Vryko Lakas on 2009-02-08
Glad we could help! 
Please remember to add "Solved" to the thread title. :)

---

### Post by igor1102828 on 2010-02-12
Guys, I am under Ubuntu 8.10 and  still cannot find the location of the files, which I'd like to remove from the trash; I do see them there, cannot remove directly because they happened to be under the root priviliges.
The folders  ***/home/myUSERNAME/.local/share/trash/files*** (and ***/info***)
are empty (***ctrl-h*** is pressed in order to make hidden files visible and I do see all of them indeed). BUT I don't have neither ***/root/local***, nor ***/root/.local***, so, [COLOR="Red"]these files[/COLOR] are, certainly, [COLOR="Red"]not in the suggested place[/COLOR]
***/root/local/share/trash/files*** (and ***/info***).
**[COLOR="DarkRed"]Where else[/COLOR]** the trash containers are placed **[COLOR="DarkRed"]in the Ubuntu 8.10[/COLOR]** ?
Thanks

---

### Post by lavezarez on 2010-03-21
This worked for me, too. Thanks for the post!

In a terminal window,
```
gksudo nautilus
```

then in Nautilus menu -
```
View - Show Hidden Files
```

and navigate to this path -
```
root/.local/share/Trash/files
```

selected the files, and pressed Shift+Del, and confirmed to delete permanently.

Then navigated to this path -
```
root/.local/share/Trash/info
```

and deleted the files the same way.

---


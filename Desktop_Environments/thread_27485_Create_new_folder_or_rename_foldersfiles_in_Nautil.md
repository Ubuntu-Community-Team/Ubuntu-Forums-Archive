---
title: "Create new folder or rename folders/files in Nautilus is broken"
date: 2005-04-16
forum: Desktop Environments
---

### Post by vtrac on 2005-04-16
I've got "Always open in Browser Windows" checked because I hate the multi-window default layout of Nautilus.  So anyway, when I go to "File" -> "Create Folder" or right-click and "Create Folder", a new folder is recreated called "untitled folder".  The "untitled folder" is selected for about 1 second where you are able to rename it something useful, but then for whatever reason it just accepts.  Even if I click on it, and go to "rename", it only gives me about 1 second before whatever I've managed to type gets accepted.  So, it is impossible to rename a folder in Nautilus, and I have to resort to opening a terminal to do it using 'mv'. 

BTW, this is true for all renames, not just folders.  Has anyone else experienced this?

---

### Post by kassetra on 2005-04-16
[QUOTE=vtrac]Even if I click on it, and go to "rename", it only gives me about 1 second before whatever I've managed to type gets accepted. So, it is impossible to rename a folder in Nautilus, and I have to resort to opening a terminal to do it using 'mv'. 

BTW, this is true for all renames, not just folders.  Has anyone else experienced this?[/QUOTE]

No, I've never had this happen - except once - when I moved my mouse off of the selection area...

Have you tried not moving your mouse while you are renaming?  Also, you might want to check and see if you have a stuck key on your keyboard or mouse...

---

### Post by perebcn on 2005-04-21
I have the same problem...
I've tried 'dpkg-reconfigure nautilus' and it doesn't work anyway!!     :?

---

### Post by Bachus on 2005-05-02
I have this problem, too.  It's very inconsistent--some times it'll work fine, but that's rather rare.

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=vtrac]I've got "Always open in Browser Windows" checked because I hate the multi-window default layout of Nautilus.  So anyway, when I go to "File" -> "Create Folder" or right-click and "Create Folder", a new folder is recreated called "untitled folder".  The "untitled folder" is selected for about 1 second where you are able to rename it something useful, but then for whatever reason it just accepts.  Even if I click on it, and go to "rename", it only gives me about 1 second before whatever I've managed to type gets accepted.  So, it is impossible to rename a folder in Nautilus, and I have to resort to opening a terminal to do it using 'mv'. 

BTW, this is true for all renames, not just folders.  Has anyone else experienced this?[/QUOTE]
 Most likely it is some mouse/keyboard problem- but difficult to diagnose. Do you have difficulties with other mouse functions - e.g., selecting a text in gedit and the typing to replace it?

---

### Post by Michele Moglia on 2005-05-16
I have the same problem, F2 works fine but if I left-click I have only one second to change the name.
Everything else works fine.


Michele

---

### Post by mrsad on 2005-05-16
same problem here. selecting rename with the mouse seems impossible to do.

---

### Post by neighborlee on 2005-05-16
[QUOTE=mrsad]same problem here. selecting rename with the mouse seems impossible to do.[/QUOTE]
-----------
I am not experiencing this problem now nor have I ever.  Are you all running a new hoary install or did you upgrade maybe from hoary RC to hoary via dist-upgrade maybe ?...I guess the mouse/keyboard thing is possible as well meaning are you using some non-standard mouse/keyboard combo ....wireless maybe ?..I could see that causing some mischief maybe..try changing out your keyboard/mouse individiually and see when things start working again...


cheers
neighborlee

---

### Post by shakin on 2005-05-16
I believe there is a Nautilus option to disable renaming inline (so you'll be presented with a popup box instead). Maybe give that a try.

I'm running KDE at the moment so I can't tell you specifically where to look for this setting.

---

### Post by Petrush on 2005-06-06
I have the same problem, only on my FAT32 partition not my home folder. Strange and annoying, but thanks for the F2 solution.

---

### Post by LodeRunner on 2005-07-04
Same problem here, too.  It's somewhat erratic--if I'm persistent, it will eventually give me 3-4 seconds to type in the file name instead of <1.  F2 appears to work fine, though (thanks Michele.)

Running latest Hoary on a Compaq laptop.  Touchpad deactivated--using a Kensington mouse.

---

### Post by vtrac on 2005-07-04
This is obviously a bug.. has someone submitted a bug report?

---


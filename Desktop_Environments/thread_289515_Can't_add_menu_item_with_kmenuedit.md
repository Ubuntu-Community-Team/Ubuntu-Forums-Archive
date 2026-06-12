---
title: "Can't add menu item with kmenuedit"
date: 2006-10-31
forum: Desktop Environments
---

### Post by me1on on 2006-10-31
I installed Kubuntu Edgy about a week ago and everything is great, but I have a problem. I can't add anything to the K Menu using kmenuedit (the menu editor that appears when you right-click the K Menu and click Menu Editor). I can remove items from the menu and add or remove separators from the menu, but nothing happens when I add something onto the menu or drag a .desktop file onto the menu editor (it appears in the menu editor but nothing happens to the menu when I save it). When I click the "New Item" button, the dialog pops up asking for the item name, then, once the name is entered, all the text fields for the item are blank (including the name field). I enter all the required information in the text fields, click "Save", and no changes are made to the K menu.

Here is the terminal output:
```

melon@melon-desktop:~$ kmenuedit
*[enter menu item name here]*
melon@melon-desktop:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x22003e7
*[save menu here]*
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2200498

```

I didn't have this problem on Dapper, and I don't know how to fix this. It could have been caused by using Automatix2 or editing my xorg.conf file, I'm not sure. Is anyone else having the same problem? Any help would be appreciated! :)

Edit: The menu editor works fine with a different user, but not mine. :(

---

### Post by me1on on 2006-10-31
Nobody knows? :( Is there any other way of adding items to the menu then?

Edit: Menu items still appear automatically when I install an application. I tried removing ~/.config/menus/applications-kmenuedit.menu, /var/tmp/kdecache-melon/ksycoca, and /var/tmp/kdecache-melon/ksycocastamp (they are automatically rebuilt on reboot), but it didn't change anything...

---

### Post by me1on on 2006-10-31
After a while of searching, I'm thinking that this might be a permissions problem. Am I supposed to have ownership over everything in my home folder? I made sure I have ownership of everything in /var/tmp/kdecache-melon/, but there are some files in my home directory that are owned by root. Here is the output of 'ls -lAR |grep root':
```
ls: ./.gnome: Permission denied
drwxr-xr-x  2 melon root   4096 2006-10-30 13:08 .automatix
drwx------  3 root root   4096 2006-10-26 21:09 .gnome
-rw-r--r-- 1 melon root 198723 2006-10-30 13:08 activity.log
-rw-r--r-- 1 melon root    133 2006-10-30 13:08 installed
-rw-r--r-- 1 melon root      1 2006-10-30 13:08 sc
-rw-r--r-- 1 melon root   1946 2006-10-30 13:08 sources_backup.list
-rw-r--r-- 1 melon root      1 2006-10-26 17:56 user
-rw------- 1 root root  444 2006-10-26 21:09 googleearth.desktop
-rw-r--r-- 1 melon melon  6082 2006-10-28 23:23 root.desktop
-rw-r--r-- 1 melon melon  21274 2006-10-26 20:14 folder_root.png
-rw-r--r-- 1 melon melon  1087 2006-10-26 20:14 folder_root.png
-rw-r--r-- 1 melon melon  1943 2006-10-26 20:14 folder_root.png
-rw-r--r-- 1 melon melon  2978 2006-10-26 20:14 folder_root.png
-rw-r--r-- 1 melon melon  5223 2006-10-26 20:14 folder_root.png
-rw-r--r-- 1 melon melon  7781 2006-10-26 20:14 folder_root.png
ls: ./.local/share/applications: Permission denied
ls: ./.local/share/mime: Permission denied
drwx------ 2 root root 4096 2006-10-26 21:09 applications
drwx------ 4 root root 4096 2006-10-26 21:09 mime
```

I am particularly suspicious of the googleearth.desktop file (I installed Google Earth through Automatix2) because when I run kbuildsyscoca (as suggested in a few other threads I've read), I get:
```
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: Invalid Service : googleearth.desktop
kio (KSycoca): ERROR: No database available!
```

Anyways, I really have no clue what I'm doing. :( Should I just change the permissions of the files in my home directory that are owned by root and give me ownership of them?

EDIT: Problem solved! Turns out that there were about 6 different googleearth.desktop files in my home directory that were all owned by root and for some reason the menu editor didn't like that. I just changed the owner from "root" to "melon" and that fixed it!

---

### Post by Wittmonn on 2007-01-24
Hello,

i have exactly the same problem with edgy. You wrote that your problem has been solved.
So, only for my understanding: You changed the owner of the googleearth-files from root to your username. After that you were able to add new menu-entries. Is that right???
I will try that after work...

---

### Post by ingo on 2007-03-10
Hi,

I am suffering the same fate, but my googleearth files are not root. Also, any attempts at editing kmenu are futile :(

This is what happens to me when I try to rebuild ksycoca

> ingo@dicker:~$ kbuildsycoca
kbuildsycoca running...
Reusing existing ksycoca
Invalid entry (missing '=') at /usr/share/services/screenkast.desktop:4
kio (KService*): WARNING: The desktop entry file screenkast.desktop has Type=Application but is located under "services" instead of "apps"
kio (KService*): WARNING: Invalid Service : screenkast.desktop
kio (KService*): WARNING: Invalid Service : googleearth.desktop
kio (KService*): WARNING: The desktop entry file Games/FreeCol/FreeCol Website.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : Games/FreeCol/FreeCol Website.desktop
kio (KService*): WARNING: Invalid Service : /usr/share/applications/kde/katalog.desktop
kio (KSycoca): ERROR: No database available!

---


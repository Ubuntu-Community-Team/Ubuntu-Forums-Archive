---
title: "cant install new theme"
date: 2005-07-27
forum: Desktop Environments
---

### Post by blu.gecko on 2005-07-27
I tried to install this theme and it told me ivalid package.

[http://gnome-look.org/content/show.php?content=26632](http://gnome-look.org/content/show.php?content=26632)

need help. :-#

---

### Post by Perfect Storm on 2005-07-27
Extract it and move the folder to /home/<username>/.themes

now open theme manager and it should be there.

---

### Post by blu.gecko on 2005-07-27
tried that, file format is invalid.

what next?   [-X

---

### Post by majikstreet on 2005-07-27
see below, I made it into a tar.gz for you.

---

### Post by majikstreet on 2005-07-27
Or...

I made it into a .tar.gz and you can just do the normal .tar.gz command, eg:
tar -zxf filename.tar.gz

It's attached.

---

### Post by blu.gecko on 2005-07-27
thanks for the help, but the problem the same, same error.

---

### Post by darkmatter on 2005-07-27
[QUOTE=blu.gecko]thanks for the help, but the problem the same, same error.[/QUOTE]

Extract the archive and look at the contents. Sometimes authors improperly package their themes (extra directories). This always leads to an 'invalid format' for the theme. All components (index.theme, metacity-1, gtk-2.0,etc) should be within a single folder.

**EDIT:** just dl'd the theme in question, just as I thought, the substructure is an invalid format, the index.theme should be in the same directory as metacity and gtk. move the index.theme from the Purple Haze folder to the Purple-Haze folder (with the hyphen) and move that folder to your .themes directory. Everything works fine.

---

### Post by blu.gecko on 2005-07-27
I dunno I make a folder in my home folder labeled themes, still no luck mad 1 folder with the inder gtk2.0 and megacity1, still getting same message.

going nutts  ](*,)

---

### Post by blu.gecko on 2005-07-27
got it working, made my own tar.gz, works fine, thanks for all the help guys

---

### Post by darkmatter on 2005-07-27
[QUOTE=blu.gecko]I dunno I make a folder in my home folder labeled themes, still no luck mad 1 folder with the inder gtk2.0 and megacity1, still getting same message.

going nutts  ](*,)[/QUOTE]

blu.gecko: you don't need to make a themes folder, there is one already.

Here's a step by step:

1 - Download the Purle Haze archive to your desktop and extract the contents.

2 - You should now have two folders named Purple Haze on your desktop. Open one of the folders, then Edit->Select All Files, then Edit-> Cut Files.

3 - Open the second Purple Haze folder. Right click in the window for this folder. select Paste Files.

4 - Close the window for the folder you just pasted to. You still have two folders on your desktop for Purple Haze. One is empty. Move the **EMPTY** folder to the Trash.

5 - Open your home folder. View-> Show Hidden Files. You will see a whole bunch of folders. Find the one named **.themes** and open it.

6 - Right click the Purple Haze folder on your desktop and select Cut Files.

7 - Right click in the folder window for the **.themes**. ->Paste Files. 

Now go System -> Preferences -> Themes. In the List of themes you will see an option for Purple Haze. Click to apply.

If you still have problems with my directions, just post here and I will repackage and attach the archive in a usable format for you.

I hope this helps. :smile:


**EDIT: Ignore this post. You type faster than I do. ;-) **

---


---
title: "Detoxing Ubuntu"
date: 2006-07-22
forum: Desktop Environments
---

### Post by music_man on 2006-07-22
I have been using Ubuntu for a little while (very little) and it seems to be getting more unstable...

I think this is in part to do with the Wine stuff I have installed. I have installed a few programs using Wine (and one I installed but I can't find any of the files) and I would just like to uninstall / completely remove anything to do with Wine and any of its applications.

How can I go about doing this in a quick manner?

Also I can't seem to get new themes. It says "Invalid File Format" when I try and add them from gnome look.

Cheers

---

### Post by shawnrgr on 2006-07-22
sudo apt-get remove wine
delete the dir : /home/your-username/.wine

edit:
menu>places>search for files : include hidden : "wine"
see what you find. would probably be safe to delete anything from the search results as you already removed wine with apt-get. but examine them and make sure before you do anything crazy ;)

---

### Post by music_man on 2006-07-22
Will that get rid of all those programs I installed?

---

### Post by Thund3rstruck on 2006-07-22
Everything you installed with wine goes into ~/.wine/c/progra~1 so by deleting everything in ~/.wine you will in turn delete all the programs installed from wine. 

As for gnome-look.org, your getting invalid file format because you're either trying to add the wrong item into the wrong place or you're untarring the archives and attempting to install them. 

GTK themes are different than icon sets which are different from metacity themes, which are different from splash screens, etc, etc, etc, you get the picture. Each of these items have to be installed (drag and drop) in the proper place to not get the invalid file format error

---

### Post by music_man on 2006-07-26
I did a search for Wine but when I go to delete them it says Access denied... Is there some command thing to delete them?

---

### Post by rattlerviper on 2006-07-26
Instability happened to me under Wine as well.  Are you using Wine with a winsows based webrowser such as IE?  Just wondering.  I can't help you with the command, as I just did a fresh install to make sure I got rid of it all, and haven't had a problem since.  I'm not sure that it is possible, but it felt like I had caught a windows virus.  Everytime I would run something with Wine the whole system would freeze up.

---

### Post by shawnrgr on 2006-07-26
sudo rm ......

---

### Post by music_man on 2006-07-26
Well Wine is uninstalled and I am not using it. I just wonder why I cant remove all those Wine files.

---


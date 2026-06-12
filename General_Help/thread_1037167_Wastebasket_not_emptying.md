---
title: "Wastebasket not emptying"
date: 2009-01-11
forum: General Help
---

### Post by IcarusR on 2009-01-11
Hi, I am not able to empty my wastebasket. If I click "Empty Deleted Items" & then at "Empty all of the items from the Deleted Items folder?" click "Delete" It deletes all but one directory. If I right click & click "Delete from deleted items folder" then click "Delete" I get an error message .. "Error removing file: No such file or directory"
If I check ./local/share/Trash/files there is nothing listed.

Does anyone have any ideas how to get rid of this pesky entry ??

Thanks

---

### Post by gettinoriginal on 2009-01-11
You can try this in terminal:
```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by IcarusR on 2009-01-12
gettinoriginal, 
Thanks for the reply but have already tried that. 
There are no files listed in either ~/.local/share/Trash/files or ~/.local/share/Trash/info

Thanks

---

### Post by gettinoriginal on 2009-01-12
I had one a couple of weeks ago that I could not get rid of, just decided to ignore it.  Then one day I logged on, and it was no longer there :confused:

---

### Post by IcarusR on 2009-01-12
Yeah but this has been there for a couple of weeks already.
I found out that it is not from the local drive but a mapped samba share, shows up which ever box I use that maps the share.
Guess I live with it !

---

### Post by silverqic on 2009-01-12
Hello, I am having the same problem. Waste basket not empting but i did something and now the waste basket will not open a window. Also, all of my desktop folders are not there anymore but I have to access then through a program whether its movie palyer etc...... How can i get this fixed....

---

### Post by mgol on 2009-01-12
> **silverqic said:**
> now the waste basket will not open a window. Also, all of my desktop folders are not there anymore

Maybe You just killed nautilus in a nasty way? Close all Your windows and try:
```
ps -e | grep nautilus
```
Does it show any nautilus instance? If not, try restart Your computer, it usually helps in such cases... If not, write here back.

One more question - do You see icons on the desktop or did they also disappear? They're also handled by nautilus, so it should be connected.

---


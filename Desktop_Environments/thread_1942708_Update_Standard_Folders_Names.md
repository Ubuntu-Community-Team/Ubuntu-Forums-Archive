---
title: "Update Standard Folders Names"
date: 2012-03-18
forum: Desktop Environments
---

### Post by danialgood on 2012-03-18
today when i was logging in to ubuntu i saw a message that was saying :

your language has been changed and do you want to translate standard folders for you.

then i remembered that i have deleted Downloads,Videos,... folders last time but i didn't delete Desktop folder then i accepted that message and ubuntu created new Downloads,Videos,... folders again also it created a new desktop and all of my desktop things are removed now

i want to know is there a way to recover previous Desktop 

Help Me. There was Many Important Files.


:confused::confused::confused:

---

### Post by ajgreeny on 2012-03-18
If you can remember exactly the name of one of the files, including the letter case of the name you can use command ```
find -type f -name <*filename*>
```
If you are not totally sure of the name try ```
sudo updatedb && locate -i <*your guess of name*>
```
The output of either may give you a clue about where your files have gone; I can not believe that the system would delete all those files simply by renaming folders

---

### Post by Helen McCall on 2012-03-18
If it has deleted an old desktop, then the contents should all be found in the Rubbish Bin you will find if you launch Nautilus filemanager.

---


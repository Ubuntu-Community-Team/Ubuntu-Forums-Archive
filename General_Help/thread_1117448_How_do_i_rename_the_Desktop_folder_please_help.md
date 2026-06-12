---
title: "How do i rename the Desktop folder??? please help"
date: 2009-04-06
forum: General Help
---

### Post by s05128 on 2009-04-06
hi all
I am pretty new to Ubuntu so please help
i have recently changed my system to chinese, but now i want to change it back to english. however, not everything is back.

for instance, under my home directory, the "Desktop" folder is in Chinese, and i can not change it... 
so in terminal if i want to "cd" to Desktop, i'd have to type in chinese...(please forgive my shallow knowledge on Ubuntu if i am wrong)

help me...
thanks a lot

---

### Post by CatKiller on 2009-04-06
There might be a sensible way to actually change the system setting in the same way that it changed it from "Desktop" to the Chinese equivalent, but I don't know what it is. I know it was a standing problem for a while that certain user-visible files were defined to be in English, which didn't fit in with Ubuntu's goals, so perhaps those systems are in flux and a bug report is in order. I don't know exactly which project it should be posted against though.

In the meantime you could make a symbolic link called Desktop to whatever the Chinese equivalent is. You'd use ```
ln -s <Chinese equivalent> Desktop
``` so that **cd Desktop** would actually take you to the Chinese equivalent. A symbolic link is just another name for the same file, like an alias.

---

### Post by sekinto on 2009-04-06
The best way to do it (because it allows you to delete the Chinese folder) is to open up a text editor (there should be one in the Application > Accessories menu) and do this:
Open the file ~/.config/user-dirs.dirs (you may need to press [ctrl+h] to see hidden folders).
Change the line XDG_DESKTOP_DIR="$HOME/<some Chinese>" to XDG_DESKTOP_DIR="$HOME/Desktop".
Make a directory called Desktop in your Home folder if it isn't already made.
Move the contents from the Chinese directory to your Desktop directory.
Delete the old Chinese directory.

---

### Post by CatKiller on 2009-04-06
I knew it had to be set somewhere. Thanks sekinto.

---

### Post by sekinto on 2009-04-06
Oh, and I made a mistake and gave you extra work. You don't have to create a new folder and move the stuff, you can just rename the Chinese folder to "Desktop". *doh*

---

### Post by s05128 on 2009-04-24
thanks a lot guys, after updating to the new ubuntu, a window popped out asking me if i want to change the naming.
its all good now, thanks.

---


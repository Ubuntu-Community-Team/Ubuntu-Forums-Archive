---
title: "pSX Games Category"
date: 2010-04-12
forum: Desktop Environments
---

### Post by Wolvenreign on 2010-04-12
Hey all, I was wondering what I would have to do to make the pSX executable show up under K->Applications->Games (instead of PCSX). I can already run it fine in terminal. (Although, I do have to use ```
killall pulseaudio
``` and ```
sudo ./pSX
``` to get it to run.)


Thanks in advance!

---

### Post by Untitled_No4 on 2010-04-12
Right click on the K Menu and choose Menu Editor, find the item you want to edit and change the command field to whatever you want. 

If you want that menu item to kill pulseaudio as well you will have to write a script to do that. Create a text file, lets say myscript.sh somewhere in your home directory and type the following:
```
!# /bin/bash
killall pulseaudio
kdesudo ./pSX
```

save the file and in console go to the folder where you saved the file and type```
sudo chmod +x myscript.sh
```

and then put the path to this file in the command field in the Menu Editor.

---


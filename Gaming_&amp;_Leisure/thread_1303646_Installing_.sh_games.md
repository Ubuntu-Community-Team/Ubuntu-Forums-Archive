---
title: "Installing .sh games"
date: 2009-10-28
forum: Gaming &amp; Leisure
---

### Post by jeffchase on 2009-10-28
I play Heroes of Newerth on my windows boot, and looking at their site again discovered that I could run it on my ubuntu boot as well. I have an issue though. After doing multiple searches I haven't found a method that works for me to install it. I've tried drag-dropping the .sh file into my terminal, tried copy an pasting, tried a few different terminal commands to try to get it to work, and still am not getting anything. One of the errors I get when typing in commands is that the file or directory doesn't exist. when I drag-drop or copy-paste, the window fades to grey. Any help?

---

### Post by del_diablo on 2009-10-28
Run this where its located
```
sh *program*.sh
```
Remeber that there exists something called tab completion :P

---

### Post by jeffchase on 2009-10-28
I apologize for my ignorance, but as you understand it, this should have worked
jeffrey@jeffrey-laptop:~$ sh HoN.sh
sh: Can't open HoN.sh
but it did not. I did not change to where the file was located, because I do not know how.

---

### Post by Nevon on 2009-10-28
Is the file executable? Check by right-clicking on it, click "Properties", go to the "Permissions" tab and see whether or not the box saying "Allow executing file as program" is checked - if it isn't, check it.

After that, it should just be a matter of opening a terminal, moving to whatever directory you have saved the file in, and typing:
```
./HoN.sh
```

---

### Post by phreakyo on 2009-10-28
It sounds like you aren't in the same directory as the file. You have to find where you saved the file first, then in the terminal type

```
cd /path/to/folder/with/HoN/
```

cd stands for change directory. Alternatively, I believe if you find where the file is in Nautilus file manager, you can right click in the empty space in the folder and an option like "open in terminal" appears, which will open a terminal where you need to be. I'm not sure because I'm not using Ubuntu or Gnome.

then try the commands other people have given, and make sure to use the exact file name... if the name was HoNClient-0.1.41.sh then you should type 

```
sh HoNClient-0.1.41.sh
```

---


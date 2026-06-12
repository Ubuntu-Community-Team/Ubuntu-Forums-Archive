---
title: "[SOLVED] Can't Empty Trash"
date: 2008-09-05
forum: Desktop Environments
---

### Post by jose158 on 2008-09-05
I can't seem to empty my Trash. I have folders in there that I "don't have permissions for". I don't have a .Trash folder though so I can't delete it via terminal. The trash is in
trash:///
Any help appreciated.

---

### Post by Shazaam on 2008-09-05
Two places for trash...
/home/username/.local/share/Trash/files
/root/local/share/trash/files

---

### Post by jose158 on 2008-09-05
Thanks! I found out I had 3gb of trash files! 3GB!!!:lolflag:

---

### Post by Shazaam on 2008-09-05
Another thing about root's /trash/files that might be a bug= when you try to delete anything there a copy of what you wanted to delete is made. To actually delete it you have to highlight the file(s) and hit your Shift+Delete keys. But, it will ask if you want to actually delete the file(s).

---

### Post by keplerspeed on 2008-09-05
I had a similar problem a while ago, where I did not have permission to empty the trash, and I do believe I used this:

sudo rm -r ~/.Trash/*

see [http://ubuntuforums.org/showthread.php?t=158119](http://ubuntuforums.org/showthread.php?t=158119)

UPDATE

Actually I may have used 

sudo rm -r ~/.local/share/Trash/files/

depends on where your trash is located.

---

### Post by jcoles on 2008-09-21
I also had deleted files in the Trash that I could not remove. 

sudo rm -r ~/.local/share/Trash/files/

did the trick.

The Trash used to be in ~/.Trash. That actually made sense. 
Now that I know, I added a symbolic link so that the trash can be referred to as ~/.Trash

Nautilus and Thunar both refer to the trash with a URL: trash:///
and do not disclose the real location.

---


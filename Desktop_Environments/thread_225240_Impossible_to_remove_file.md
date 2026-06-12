---
title: "Impossible to remove file"
date: 2006-07-29
forum: Desktop Environments
---

### Post by xinelo on 2006-07-29
I couldn't delete this post myself. Could any administrator do it for me? 

Ideally, could you also add ardchoille's replies to the thread in [http://www.ubuntuforums.org/showthread.php?t=123622](http://www.ubuntuforums.org/showthread.php?t=123622) ?

---

### Post by ardchoille on 2006-07-29
open a term, run gksu nautilus, browse to the correct Trash bin on the correct device and delete it.

---

### Post by xinelo on 2006-07-31
Thanks ardchoille, 

If I open nautilus in the way you suggest, I can go to /media/sda1/.Trash-xinelo and delete de .zips directory. I was about to ask how come I can delete it that way but not from the terminal being root, when I saw that now there is a .Trash-root directory. The .zips directory is there but I can't delete it, not even from the nautilus session opened with gksu. 

By the way, I forgot to mention that the file with the long name that I want to delete appears when I open the .zips directory but it disappears as soon as I try to click on it. It really behaves weirdly. 

Thanks again. 
xinelo

---

### Post by ardchoille on 2006-07-31
In the gksudo nautilus window, File -> Empty Trash

---

### Post by xinelo on 2006-07-31
Thanks for your help, ardchoille. 

I have the same problem when I try to empty the trash in that way. 

Precisely, the error message is: 

**Error "File not found" when deleting "/media/SDA1/...o y chica..".**

Weird. 

Any other ideas?

---


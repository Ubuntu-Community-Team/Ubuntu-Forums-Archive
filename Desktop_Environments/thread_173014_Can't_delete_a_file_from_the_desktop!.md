---
title: "Can't delete a file from the desktop!"
date: 2006-05-09
forum: Desktop Environments
---

### Post by mmcmonster on 2006-05-09
Try this:
1. On the decktop, right click and Create Document -> Empty File

(A file named "new file" is created)
2. Select the file with the mouse, and hit F2 to rename the file.

3. Change the file name to ".xfile" (Notice that it starts with a 'dot'.

4. Try to delete the file. ](*,)

I managed to create two of these files on my desktop, and can't delete them now!

Can anyone please help!

---

### Post by Dr. Nick on 2006-05-09
hehe, I now need help aswell :rolleyes:

Im going to keep trying :)

---

### Post by Dr. Nick on 2006-05-09
[quote=Dr. Nick]hehe, I now need help aswell :rolleyes:

Im going to keep trying :)[/quote] 
Its gone here , right click and hit move to trash the log out/in and see what happens

---

### Post by richbarna on 2006-05-09
I did the same thing, but mine just went invisible.
So I created another one and it said .xfile already exists, do you want to overwrite? I said yes, and that one disappeared too.
weird?!

---

### Post by Ramses de Norre on 2006-05-09
rm -f Desktop/.xfile
Why couldn't you delete it? What error did it gave?
Instead of logging in & out you may be able to achieve the same by pressing ctrl-r (refresh).
The disappearing is normal, files starting with a period (.) are hidden files, press ctrl-h to show them.

---

### Post by richbarna on 2006-05-09
[QUOTE=richbarna]I did the same thing, but mine just went invisible.
So I created another one and it said .xfile already exists, do you want to overwrite? I said yes, and that one disappeared too.
weird?![/QUOTE]

To remove these files i just right click and selected "undo move".
All gone.
Easy Peasy : )

---

### Post by Dr. Nick on 2006-05-09
[quote=richbarna]To remove these files i just right click and selected "undo move".
All gone.
Easy Peasy : )[/quote]

ctrl+r works just as well as log off. even though i had  a "." infront of mine it didnt dissapear :confused: and mine is set not to show hidden files, and a ls from teh terminal doesnt show it on the desktop. Weird lol

---

### Post by mmcmonster on 2006-05-09
Thanks for all the help!

I didn't think to try logging out.

I logged out and back in, and all was well. :-)  Of course, I forgot that I was running a process in the background for the last couple hours that got lost by logging out. :-(  Well, at least I don't have those pesky icons on the desktop anymore.

---


---
title: "gwenview, konqueror and jpg"
date: 2006-07-27
forum: Desktop Environments
---

### Post by ArponerO on 2006-07-27
Hi (k)ubuntusers,

I have Kubuntu 6.06 and the jpg files are associated with gwenview. Konqueror does not show any icon besides the jpg files and after clicking whatever jpg file gwenview starts but no image is showed at all. Whenever I put the whole path to the image including its name in the gwenview location bar, the picture is shown perfectly.

Any suggestion will be appreciated.

---

### Post by Ares Drake on 2006-07-27
I got the exact same problem with Ubuntu (Gnome). Don't know whats wrong, maybe gwenview is broken? Should we file a bug report? How would that be done?

---

### Post by Ares Drake on 2006-07-28
I suppose it got something to do with permissions: I tried (de)installing / reinstalling gwenview several times - without success. It works however when I run it as root. Anyone any ideas?

---

### Post by ArponerO on 2006-09-08
It seems to be a problem with crossover (if you have this installed, of course).
The solution is simple: go to File associations and remove all crossover-jpg and crossover-jpeg references.

---

### Post by ringmaster on 2007-04-06
Thank you ArponerO!!! I was going crazy with file associations before I read this post! I had problems not only in gwenview, in previsualizations with desktop background image too...

I will explain the solution in depth for newbies:

Go to Konqueror -> Preferences -> configure Konqueror

Select on the left "File associations"

Search for "jp" and the press the button "erase" after selecting "x-crossover-jpg" under "application". Erase only "application" associations, not associations under "image"!!!

Exit konqueror, and the association is working again!!

---


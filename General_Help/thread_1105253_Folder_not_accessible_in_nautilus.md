---
title: "Folder not accessible in nautilus"
date: 2009-03-24
forum: General Help
---

### Post by krnekhelesh on 2009-03-24
Hi,

I had some important university files in a folder. I recently copied a pdf file to a folder...and since then when I try to access the folder and open a file nautilus gets stuck, and stops working.

I can access any other files in other folders except for that specific folder alone.

---

### Post by ene_dene on 2009-03-24
> **krnekhelesh said:**
> Hi,

I had some important university files in a folder. I recently copied a pdf file to a folder...and since then when I try to access the folder and open a file nautilus gets stuck, and stops working.

I can access any other files in other folders except for that specific folder alone.
It must be permission problem then. It's possible that you've copied the files to that folder as another user or root.
Right click on that folder, go to permissions, if you see "root" is the owner, than you need to change it (you'll have to do that from console). Also folder has to be executable.

---

### Post by kanikilu on 2009-03-24
Out of curiosity, are you able to view this folder from a terminal? If so, check the permissions.

Also, see if you can get to it from other file managers. For GUI you can try ones such as pcmanfm, mucommander or tuxcmd. For text based, try mc (midnight commander).

---

### Post by krnekhelesh on 2009-03-24
I right-clicked the folder and I as a user have all the permissions and also the folder is executable. But when I open the folder it is blank and I get the message
" Nautilus has stopped working." and then I force quit it.

However using the terminal the terminal I can access the folder and list the files in it.

---

### Post by kanikilu on 2009-03-24
Hmm...can you try turning off previews? In Nautilus, go to Edit > Preferences > Preview, and then set all the drop-downs to "Never".

---

### Post by krnekhelesh on 2009-03-24
Hey it worked!!!!. Thanx man....I got freaked out for a minute when I couldnt access the folder before....

Why couldnt I access it before?

---

### Post by kanikilu on 2009-03-24
Glad that worked.

Sorry, I have no idea why this happens, but I've seen it on here a few times, but never experienced it myself. I suppose someone ought to see if there is a bug report about it yet...

---

### Post by wattestaebchen on 2009-04-04
Just wanted to say I had the same problem in Ubuntu 8.10. In some directories I couldn't even create a folder any more. Nautilus freezes instantly creating a folder called "untitled folder". When trying to access this folder after killing Nautilus, Nautilus freezes instantly, starting to accumulated memory and using nearly 100% of the cpu. Only solution - kill Nautilus.
Disabling of all previews helped.

---


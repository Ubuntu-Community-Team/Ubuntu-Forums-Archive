---
title: "Cannot open home folder"
date: 2009-03-15
forum: General Help
---

### Post by Pfredpfudpucker on 2009-03-15
I have permissions, but somehow, in my installation of additional applications and drivers in Ubuntu, I have created a problem.  When I open my home folder, mplayer pops up, along with a window that says "seek failed".  The home folder doesn't open.

Any idea of 

1.) how I created this situation (so I don't repeat the error),

and 

2.) how to correct the problem so that I can open my home folder?

I can still open the home folder by going to the file system, and then open home from there.

---

### Post by perrti-y02 on 2009-03-15
By what route are you opening the home folder from in the first instance (the one that doesn't work)?

---

### Post by taurus on 2009-03-15
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
ls -la ~
```

---

### Post by drs305 on 2009-03-15
This could be related to a reported nautilus bug. Open nautilus and right click on any folder. Select "Properties" , then "Open with" and select or add "Open folder".

---

### Post by Pfredpfudpucker on 2009-03-16
I am opening the Home folder (using Gnome) by clicking on Places>Home Folder.

I opened Nautilus and checked the "open with" tab - it was set to have mplayer open the file.  I rechecked open file and it corrected the problem.

Thanks for the responses!

---


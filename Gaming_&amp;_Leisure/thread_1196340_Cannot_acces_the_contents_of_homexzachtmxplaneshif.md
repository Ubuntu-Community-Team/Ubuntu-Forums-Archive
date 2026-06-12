---
title: "Cannot acces the contents of /home/xzachtmx/planeshift"
date: 2009-06-24
forum: Gaming &amp; Leisure
---

### Post by xZachtmx on 2009-06-24
ok i have sucessfully installed planeshift for linux but when i try to launch the game it says i dont have the permission to do it and the folder has a big lock on it.  How can i get the permissions?

---

### Post by dunbrokin on 2009-06-24
> **xZachtmx said:**
> ok i have sucessfully installed planeshift for linux but when i try to launch the game it says i dont have the permission to do it and the folder has a big lock on it.  How can i get the permissions?

Under Accessories, click on the terminal. In the terminal type

sudo nautilus

This will bring up the Nautilus navigation folder. Go to where your game is and right click on it. It will show "Properties" in the table that comes up. Click on Properties and find the Permissions tab. Change from existing Access to Read and Write.

That should solve it.

---

### Post by xZachtmx on 2009-06-25
ok i put read and write for all 3... but whenever i click apply they go blank again and the dolder is still locked?

---

### Post by dunbrokin on 2009-06-25
> **xZachtmx said:**
> ok i put read and write for all 3... but whenever i click apply they go blank again and the dolder is still locked?

Did you do 

sudo nautilus ?

---

### Post by xZachtmx on 2009-06-25
yes and i put read and write.  Then when i put apply changes a few seconds later the boxes dont have read and write in them they jsut go blank again

---

### Post by dunbrokin on 2009-06-25
> **xZachtmx said:**
> yes and i put read and write.  Then when i put apply changes a few seconds later the boxes dont have read and write in them they jsut go blank again

Hmmm!...Sorry, your problem is outside my knowledge base, hopefully somebody else will pick it up.

---


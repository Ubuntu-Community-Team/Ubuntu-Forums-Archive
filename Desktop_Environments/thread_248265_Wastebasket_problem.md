---
title: "Wastebasket problem"
date: 2006-08-31
forum: Desktop Environments
---

### Post by olegc1 on 2006-08-31
I have this problem with wastebasket (or trash, whatever) always showing up empty in Nautilus even when there is actually stuff in ~/.Trash 

I've checked gconf and that seems to be correct (URI command for trash: is nautilus "%s"). If I force Nautilus to go to .Trash, it will show the deleted files, but just opening the Wastebasket from an panel applet or a desktop icon turns up nothing. 

It is a minor issue, but maybe anyone has dealt with it, or know what might be the problem.

---

### Post by aysiu on 2006-09-01
Have you tried removing the Trash applet from the panel and then re-adding it?

---

### Post by chinaski on 2006-09-05
thanks, I had a similar problem but reversed, trash empty but icon showing full

the thing of removing and adding it did the trick ;)

---


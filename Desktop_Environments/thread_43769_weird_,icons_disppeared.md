---
title: "weird ,icons disppeared"
date: 2005-06-23
forum: Desktop Environments
---

### Post by wxm505 on 2005-06-23
After I reinstalled Hoary, I copied all the files which I backed up from 
my previous box to the /home .Something are running ok except
all the icons on the panel(top and bottom)disppeared.
I added them again and then log out. It happened again.
all the icons including main main ,windows list had all gone
also the size of top panel was resized to twice wide as original.
Where can I find the place to configure them , make them
be there permenantly ? Or anything wrong with what I did?
thanks a lot

---

### Post by Alexander Kirillov on 2005-06-23
[QUOTE=wxm505]After I reinstalled Hoary, I copied all the files which I backed up from 
my previous box to the /home .Something are running ok except
all the icons on the panel(top and bottom)disppeared.
I added them again and then log out. It happened again.
all the icons including main main ,windows list had all gone
also the size of top panel was resized to twice wide as original.
Where can I find the place to configure them , make them
be there permenantly ? Or anything wrong with what I did?
thanks a lot[/QUOTE]
 One possibility I see is that among files you copied, there are various config. files that describe your panel etc - and it is possible that after reinstalling, when you copied files back, they now have wrong permissions or owner (probably, your user ID on new system is different from what it was in the old one). Depends on how you backed up and restored them. 

Try to look at the directories and files: 
.gnome*
.gconf*
and check the ownership/permissions for all of them. If the owner is wrong, here is your problem.

A radical way of fixing it would be removing (or renaming) all of these directories (from text console, not from within GNOME). Then, when you login again, they will be recreated with correct attributes. Of course, this way you will have to recreate all your GNOME customizations (panels, applications preferences, etc).

---


---
title: "USB Flash drive on Desktop ?"
date: 2006-02-13
forum: Desktop Environments
---

### Post by gtdj on 2006-02-13
I just upgraded breezy to dapper few weeks ago. I notice that my USB Flash drive which used to automount and place there shortcut in to desktop is disappeared ! (Automount but its shortcut isn't be placed on Desktop) :confused: 

For me it's hard time to go to terminal and make it umount before I plug it out. :( 

How to get it back ?

---

### Post by nalmeth on 2006-02-13
You should probably post in the dapper forum for this, breezy users probably wouldn't know

Dapper Drake Development release Forum:
[http://www.ubuntuforums.org/forumdisplay.php?f=111](http://www.ubuntuforums.org/forumdisplay.php?f=111)

---

### Post by gtdj on 2006-02-13
so sorry :cry:

---

### Post by nalmeth on 2006-02-13
haha, yes you should be ashamed! 

Just joking, good luck with that though!

---

### Post by mcduck on 2006-02-13
Try opening Configuration Editor (I think it's hidden in dapper by default, so either enable it with Menu Editor or run 'gconf-editor' in terminal.

Then browse to apps/nautilus/desktop and make sure that 'volumes_visible' is marked. Also you might want to have a look at system/storage, there are some more options.

---


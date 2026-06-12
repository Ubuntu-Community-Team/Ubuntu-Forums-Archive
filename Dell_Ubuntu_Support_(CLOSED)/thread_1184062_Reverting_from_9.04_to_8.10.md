---
title: "Reverting from 9.04 to 8.10"
date: 2009-06-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adjock12 on 2009-06-10
Hi,

I was wondering if I were to revert my system from 9.04 to 8.10 would I lose all of my data? Would I have to uninstall 9.04 or is there some way to revert it? Also where would I find the 8.10 version to revert to. If I would lose all my data is there any way to save it all before putting 8.10 on my computer. It is a Dell Latitude D600.

Thanks

---

### Post by jaqrah on 2009-06-11
Well...if you set up a / and /home partition, it will be quite easy.  Re-install 8.10.  When you get to the step for partitioning, choose manual.  You will have to re-partition your / partition to re-install 8.10.  You will NOT want to touch your previous /home partition.  Make absolutely sure you do not format your /home partition or you will lose everything on your /home partition.

Quite frankly, you should back-up all of your files anyway just in case you make a mistake.

If you do not have a separate / and /home,you will need to back up you files and re-install from scratch.  I would google or search the forum for directions on setting up a / and a /home partition.  It will make your life easier if you want to re-install or do a clean install in the future.

The following site will provide a direct tutorial for installing 8.10 on a  dell mini 9 including how to set up a / and /home partition during setup.  Obviously, you don't have a mini 9 but it will help you with the basic concepts.

[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

Good luck

---

### Post by tyroeternal on 2009-06-11
Have you considered finding some kind of backup solution?  This is a wise practice to use in general, and would help you out a lot if you want to flip to a different release.  Reverting to 8.10 is not going to be an option as far as I am aware.

Even a simple solution like burning files to a dvd/cd or using dropbox ([http://getdropbox.com](http://getdropbox.com)) will help you save some of your files and bring them over to your next install.

---


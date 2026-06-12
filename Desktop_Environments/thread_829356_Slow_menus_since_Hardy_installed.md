---
title: "Slow menus since Hardy installed"
date: 2008-06-14
forum: Desktop Environments
---

### Post by bdalzell on 2008-06-14
This did not start when I installed Hardy a month ago but it has become much worse in the last week.

After gnome GUI appears and is fully displayed it takes around 20 to 30 seconds before I can activate anything from an icon. 

Then if I have gedit opened and I do a "save as" it may take over a minute for the save as widget to be useable.

I can live with the slow access to the gnome desktop at boot up but these sluggish gedit menus are driving me nuts as I do a lot of writing.

---

### Post by dehuszar on 2008-06-27
I'm having the same problem.  It happened after an update of Google Earth, but after having uninstalled it entirely, no change.  My guess is the timing is coincidental.

Anyone else seeing this?

---

### Post by hrstrand on 2008-06-27
I solved a similar ( possible same ) issue by the suggestion in this thread : 

[http://ubuntuforums.org/showthread.php?t=811795](http://ubuntuforums.org/showthread.php?t=811795)

For me, it turned out it was an invalid reference to a folder on an non-existing intranet that caused the delays

/Peter

---

### Post by bdalzell on 2008-06-30
I deleted the Places>Bookmarks folder contents. However I am suspicious that files listed under Places>Recently Used in the Open Files dialog might also be contributing to the slow menus if those files have been moved or deleted.

Anyone have any ideas on this possibility? I have not figured out how to delete things from Places>Recently Used

---

### Post by dehuszar on 2008-07-01
I'm afraid I don't have an answer for you.  For me, it was trying to connect to a server share that was no longer available.  Removing the share as recommending in the link above worked brilliantly.

Sam

---

### Post by bdalzell on 2008-07-12
I finally solved it. I opened System>Preferences>Sessions and selectively turned off startup programs. With Tracker and Tracker Applet turned off the menus are coming up with normal speed.

Seems to me that I had problems with Beagle under Feisty - it eventually filled up my hard drive with its index (around 15 GB). 

So far none of these GUI indexers seem to be able to match the command line locate command.

---

### Post by dbera on 2008-07-12
> **bdalzell said:**
> 
Seems to me that I had problems with Beagle under Feisty - it eventually filled up my hard drive with its index (around 15 GB). 

So far none of these GUI indexers seem to be able to match the command line locate command.

Feisty ... Gutsy ... Hardy ... Intrepid (nearly there)
Maybe its time to try again :-)

---


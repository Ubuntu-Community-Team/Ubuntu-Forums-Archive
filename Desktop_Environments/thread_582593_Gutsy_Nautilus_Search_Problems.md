---
title: "Gutsy Nautilus Search Problems"
date: 2007-10-20
forum: Desktop Environments
---

### Post by pt123 on 2007-10-20
Now if I navigate to a folder

eg. /media/pics

Then do a search it doesn't search for items in the folder and sub-directories below, but it is just using tracker's indexed files. 

Which is ridiculous if not stupid. Even Windows XP search is not this useless. 

Is there a way to separate these two functions (tracker & nautilus) , if I navigate to a folder and then do a search all I want is results with in the folder.

---

### Post by PsychoBrat on 2007-10-21
Seconded.

When I noticed that it was still doing this, I just killed Tracker altogether - not worth the frustration for the minimal use I have for it.

---

### Post by pt123 on 2007-10-22
Yeah what is annoying is that before you could navigate to the /usr/share/icons folder

and search for contact-new.png and you will get all the varieties of it in thumbnails.

They don't expect to index our root folder.

Also if you search for a general term like you  .jpg you will get a zillion results. 

They should have given an option in Nautilus whether to user tracker or not.

There are 2 bugs filed for this 

[https://bugs.launchpad.net/ubuntu/+bug/154692](https://bugs.launchpad.net/ubuntu/+bug/154692)

[https://bugs.launchpad.net/bugs/150379](https://bugs.launchpad.net/bugs/150379)

---

### Post by pt123 on 2007-10-27
There is a some what of a work around,
An application called nautilus-search-tool 

[http://saettaz.altervista.org/software/nautilus_search_tool.html](http://saettaz.altervista.org/software/nautilus_search_tool.html)

Deb
[http://www.getdeb.net/app.php?name=nautilus-search-tool](http://www.getdeb.net/app.php?name=nautilus-search-tool)

That lets your right click on folder and search in it. It brings the search dialog found under places, it sets the folder for you so you don't have to browse.

---

### Post by alecz20 on 2008-07-19
I saw the Idea at:
[http://brainstorm.ubuntu.com/item/476/](http://brainstorm.ubuntu.com/item/476/)
and the bug report at:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/148701](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/148701)

Both they  either "idea implemented" or fix released, however even having all updates it is still broken on my system.

How can I get it fixed without recompiling Nautilus?

---


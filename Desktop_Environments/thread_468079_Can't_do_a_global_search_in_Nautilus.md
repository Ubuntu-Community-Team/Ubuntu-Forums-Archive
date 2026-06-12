---
title: "Can't do a global search in Nautilus?"
date: 2007-06-08
forum: Desktop Environments
---

### Post by timzak on 2007-06-08
I'm a newbie here, so if I'm off-base, please set me straight.  I've noticed when I'm navigating through Nautilus and try to search my system for a particular file or folder, it only searches the directory it's currently in.  To do what I want, I have to go to Places->Search.  Shouldn't the search function be integrated into Nautilus?  Am I doing something wrong, or is there really no way to do a global search in Ubuntu's default file system?

---

### Post by ticopelp on 2007-06-08
Try installing beagle, aka Desktop Search. Much more powerful and useful than searching in Nautilus.

```
sudo apt-get install beagle
```

---

### Post by timzak on 2007-06-08
Thanks.  The Search function in the Places dropdown menu works just fine.  I wasn't looking for a better search program, I was just wanting to confirm that Nautilus cannot search outside of the directory it's currently in.  I thought maybe I was doing something wrong.  Can someone confirm whether or not Nautilus can do a global filesystem search, or is it limited to the directory it's currently in?

Thanks.

---

### Post by ticopelp on 2007-06-08
I believe that's the case; however, you could probably just go to your /home/ or / directory and run the search from there; that would be the same as the global search. 

I only recommended beagle because I find the search function in Nautilus to be far too picky and clunky. Best of luck.

---

### Post by timzak on 2007-06-08
> **ticopelp said:**
> I believe that's the case; however, you could probably just go to your /home/ or / directory and run the search from there; that would be the same as the global search. .

I tried, and did not find that to be the case.  It seemed to completely ignore the contents of folders while in home or root.  I had to physically launch the "search" applet in Places in order to search within directories.  Search seems to be a separate program from Nautilus; otherwise one would think you could do the same search while in a Nautilus window.

---

### Post by vjones777 on 2007-08-18
I think that the default (for a new install) is for nautilus to only search starting at the users home directory.  You can see what its searched after you get the search results - click on the '+' and it will probably show 'Location' as being the user.  You can change that to 'Filesystem' to search all your drive.  You can also add other search filters there.  That will work for your current search.

To change the default behaviour (on ubuntu 6.06) go to System-Preferences-Search&indexing.  On the Indexing tab, click on '+' and add the directories you want to be searched by default.   If you select 'Filesystem' it will show under name as '/'.

I'm guessing that this is a per user setting but I havn't verified that.

On 7.04 I've heard they've moved search and indexing somewhere else. :confused:

---


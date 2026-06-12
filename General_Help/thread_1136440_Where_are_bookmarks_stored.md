---
title: "Where are bookmarks stored?"
date: 2009-04-25
forum: General Help
---

### Post by crazypeppo on 2009-04-25
Where at on HDD are bookmarks saved? What file?
I want to import/copy favorite websites from HDD to new install HDD.

---

### Post by Synthros on 2009-04-25
Are you referring to bookmarks in Firefox?  If so, you would just need to launch Firefox, go to Bookmarks-->Organize Bookmarks-->Import and Backup-->Backup, then just specify the location you want to save the file to.  Once you're ready to restore your bookmarks, you would just follow the same steps, but click on Restore and locate the backup file that you created.

---

### Post by lisati on 2009-04-25
Another way is use a firefox addon called ["Xmarks"]("http://xmarks.com") (it used to be called foxmarks). I use this to keep the bookmarks on my machines synchronised, and it comes in handy when I've needed to reinstall. It can be installed by clicking on Bookmarks->get bookmarks addons. More information can be found [here]("http://xmarks.com")

---

### Post by kaibob on 2009-04-25
> **crazypeppo said:**
> Where at on HDD are bookmarks saved? What file?...

Bookmarks in Firefox 3.x are stored in:

/home/username/.mozilla/firefox/uniquenumber/places.sqlite

---

### Post by crazypeppo on 2009-04-25
@ Synthros - Thank you, but I can't boot my original HDD with the bookmarks on it.
@ Lisati - Thanks, haven't seen that have to give it a try maybe help prevent my situation next time.
@ Kaibob - Thanks thats what I was looking for! But I tried copying the file and moving it to the new HDD and no bookmarks showed up. Is it possible to do it that way?

---

### Post by kaibob on 2009-04-25
> **crazypeppo said:**
> 
@ Kaibob - Thanks thats what I was looking for! But I tried copying the file and moving it to the new HDD and no bookmarks showed up. Is it possible to do it that way?
I do it that way all the time. The only difference is that I restore an older drive image and then copy the bookmark file from a recent backup of my home directory. Perhaps the new install makes a difference?

---

### Post by Zimmer on 2009-04-25
prior to FF 3 the bookmarks were in a file  bookmarks.html

I believe you could import that file to FF 3 
by

Opening FF
choose  Bookmarks>Organize Bookmarks>
Then choose Import & Backup  and select import HTML to go find the bookmarks.html file

---

### Post by crazypeppo on 2009-04-26
Cool deal that worked...I had to play around with some files...Thanks!

---


---
title: "[SOLVED] Looking to limit the total size of .thumbnails"
date: 2008-12-17
forum: Desktop Environments
---

### Post by maxpoweron on 2008-12-17
Is there a way to limit the size in MB of .thumbnails?

---

### Post by gettinoriginal on 2008-12-18
The only answer I know of is to change them in gimp.  :p

---

### Post by maxpoweron on 2008-12-18
I don't think I explained myself clearly.  I want to set a total folder size of .thumbnail to 20 MB.  When the folder reaches that size, the oldest files will be deleted.  Like setting the cache size in IE or Firefox.

---

### Post by gettinoriginal on 2008-12-20
Sorry to take so long to respond.  Make sure that configure editor is installed from synaptic.  Go to applications, system tools, and initiate it.   Desktop > Gnome > Thumbnail_cache,  highlight it, right click, edit.  Hope that helps   :P

---

### Post by maxpoweron on 2008-12-22
That worked!  Thanks for the info.

---

### Post by FreddieMacelvoy on 2013-02-06
The key was set to 512 in config editor,  but my .thumbnails was 916MB.  Any thoughts why?

-Fred

---

### Post by wildmanne39 on 2013-02-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


---
title: "Vuze/Azureus fails to update"
date: 2009-06-11
forum: General Help
---

### Post by Bigtime_Scrub on 2009-06-11
So I installed Vuze from the repositories but I kept getting this update notification popping up. I kept trying to update and it wouldn't do it. It would say that it updated but the update kept popping up saying it still needed to be done. 

So I got rid of it with the purge command and then did an autoremove to make sure it was gone and I downloaded Vuze directly off their site as a .deb package. 

Now when I try to update it says it failed. I tried the method found here [http://www.azureuswiki.com/index.php/Failed_Update]("http://www.azureuswiki.com/index.php/Failed_Update") but I'm still getting no love and I really like Azureus and I want to download and check out the new Fedora 11 with a torrent. 

Any ideas on what to do?

---

### Post by Bigtime_Scrub on 2009-06-11
I figured it out!

What was going on is that Vuze created a 
usr/share/vuze directory in root where the updates would go.

Then it could not update because as a user you do not have permission!

So what I did was 
```
gksu nautilus
``` and I modified the permissions to allow Vuze to do its thing. It updated and installed everything correctly and now it is working great and it looks even better than before.

---


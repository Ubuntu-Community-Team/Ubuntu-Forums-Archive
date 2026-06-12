---
title: "XFCE complete removal -&gt; all files in my home directory are gone"
date: 2009-12-13
forum: Desktop Environments
---

### Post by chaperone on 2009-12-13
Hey guys,
I thought a XFCE complete removal is my case a good idea, cos I was using GNOME anyways. So I decided to remove it (complete removal of XFCE) and to perform a reboot. After the reboot all my files in /home/user were gone and I had a maiden home directory again. ****! (so no files, no bookmarks, no configured apps)

the interesting thing is that the files of an other user in /home/ are untouched and still there! How can this happen? Any ideas what I can do in such a case? Well, I think my files are gone :)

thanks for your help,

Sebastian

---

### Post by XubuRoxMySox on 2009-12-13
Xfce takes alot of stuff with it when it is deleted - "completely removed," it may take many Gnome dependencies too.

When people do a fresh install, it is the /home *partition* that is preserved (assuming the original setup was manual and the "format this partition" box is un-checked), not the /home *directory*.

-Robin

---

### Post by chaperone on 2009-12-13
thanks Robin for your reply. I had a deeper look into it and have seen that the files weren't deleted, but encrypted. So the system has  probably problems to identify me. 

I performed the ecryptfs-mount-private command with my pwd and it worked. Puh :)

Thanks again for your help!!

Cheers, Sebastian

---


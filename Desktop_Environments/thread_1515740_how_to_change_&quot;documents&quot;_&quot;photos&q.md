---
title: "how to change &quot;documents&quot; &quot;photos&quot; to windows partition?"
date: 2010-06-22
forum: Desktop Environments
---

### Post by etheesdad on 2010-06-22
Hi.. Sorry this is a hopeless n00b question. Ive tried googling, but as you can imagine, *windows, linux, documents, location* and alternative variants are mostly about samba and this question relates to how gnome identifies the location of 'documents' 'pictures' and 'music'. 

In Windows it was a matter of simply moving the folder Location in Properties. I cant seem to figure out how to use the 'documents' 'pictures' etc in my NTFS partition to mesh up with their equivalents in Linux. 

Many thanks for any help with this.

---

### Post by etheesdad on 2010-06-23
Is it really so difficult that *no-one* knows how to do it?

---

### Post by kornfan71 on 2010-06-23
You *should* be able to make a symbolic link to the NTFS folders.
So, something along the lines of:
"ln -s /media/NTFS_PART/<directory to pictures folder> ~/Pictures"
The one downfall to this is that the NTFS partition _must_ be mounted (preferably at startup), otherwise your ~/Pictures directory wouldn't exist....

---


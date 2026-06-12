---
title: "copying/backing up user profiles"
date: 2009-05-05
forum: General Help
---

### Post by dstarfire on 2009-05-05
What's the best way to copy or backup a user's profile, so that it can be restored on a fresh install? 

I tried using rsync to copy all the files to another drive, but that resulted in an empty desktop (no panels, new launcher dialog broken) and much headache. 

Is there a safe or 'proper' way to do this?

---

### Post by dcstar on 2009-05-05
> **dstarfire said:**
> What's the best way to copy or backup a user's profile, so that it can be restored on a fresh install? 

I tried using rsync to copy all the files to another drive, but that resulted in an empty desktop (no panels, new launcher dialog broken) and much headache. 

Is there a safe or 'proper' way to do this?

All hidden files have to be selected and copied, you can manually do this or use a tool like Unison.

Personally, a separate /home partition is the best way to retain this data as installations do not touch it.

---

### Post by dstarfire on 2009-05-07
I've tried manually copying all the hidden files, and somehow that ended up corrupting the destination profile (got an error message, or a totally blank desktop). Are there some files/folders that can't be safely copied this way?

As for the seperate /home partition, do I need to do anything special to make ubuntu import the settings once I've set that as a user's home folder?

---

### Post by mcduck on 2009-05-07
You will probably have to leave .ICEauthority and Xauthority files out of the backup (not that you'd even need them).

Also one thing you should consider is the ownerships/permissions of the files. You'll want to make sure they stay the same. Saving the backup as a .tar.gz archive is a nice way to do this, as that way the permissions will be kept. Even if you move the backup to some (Windows) file system that can't normally store Linux-style permissions and ownerships.

---

### Post by dstarfire on 2009-05-07
That would explain my difficulties as I was indeed trying to store the profile backup on a windows fat32 partition. 

I'll give your archive idea a shot, and hopefully it'll work. 

Thanks again, for your help.

---


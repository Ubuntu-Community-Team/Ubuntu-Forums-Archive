---
title: "permissions problems after apt-get upgrade"
date: 2005-04-09
forum: Desktop Environments
---

### Post by linuxgrrl on 2005-04-09
hi,
I've been running Hoary for a few months (not upgrading it all that regularly).  Yesterday I did apt-get upgrade, and now I am having problems with file permissions.  For example, user "mythtv" is no longer able to access my photo collection, which is mounted under /home/mary/photos, even though the folders and their contents all have permissions "rwxrw-rw-"   

I don't understand all that much about permissions, except that these files used to be accessible before, and now suddently they aren't.  [i know it happened with my upgrade, because my desktop was one of those photos and now it's gone :)]  Why would files labeled "rwxrw-rw" suddenly not be readable, and in fact arent even viewable, by user mythtv? 

TIA,
Mary

---

### Post by linuxgrrl on 2005-04-09
[QUOTE=linuxgrrl]hi,
  [i know it happened with my upgrade, because my desktop was one of those photos and now it's gone :)]  Why would files labeled "rwxrw-rw" suddenly not be readable, and in fact arent even viewable, by user mythtv? 

TIA,
Mary[/QUOTE]

okay, I guess there is one other thing i did while upgrading.  I added user mythtv to the group "cdrom'.  but that shouldn't decrease mythtv's other permissions, should it?

---


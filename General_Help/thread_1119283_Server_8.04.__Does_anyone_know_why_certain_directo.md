---
title: "Server 8.04.  Does anyone know why certain directories are limited on space?"
date: 2009-04-07
forum: General Help
---

### Post by Linuxwho? on 2009-04-07
Hi all,

I created a directory under the "dev" directory and then tried to "untar" a 400mb file to it.  It told me I was out of space when I know that is false because I had 12gigs left on the drive itself.  Any ideas?

---

### Post by john.soper on 2009-04-07
Check to see if the user you are logged in as has permissions to write in that directory.

---

### Post by Linuxwho? on 2009-04-07
Thanks.  I used sudo su which gives me permission as admin until I logoff.

---

### Post by dcstar on 2009-04-08
> **Linuxwho? said:**
> Hi all,

I created a directory under the "dev" directory and then tried to "untar" a 400mb file to it.
......

The /dev folder is a system folder and you should not be creating folders or putting files in it.

You will be much better off not touching any system folder, just make your own folders outside the system folders.

---

### Post by Linuxwho? on 2009-04-08
Thanks.  Yes I understand this,noiw but I was wondering why it was limited in space and if there are any other folders that are limited like this?

---


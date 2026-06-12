---
title: "Bacula to DVD"
date: 2005-01-05
forum: General Help
---

### Post by nocturn on 2005-01-05
Is it possible to get Bacula to write to DVD's ?

---

### Post by Ste on 2005-01-05
There's a feature in this months LinuxFormat about backing up.
Bacula is capable of writing to DVD. Not sure how it's done however as I couldn't get an archiever to install as of yet.


[http://www.bacula.org/html-manual/index.html](http://www.bacula.org/html-manual/index.html) -- might be a bit more help.

---

### Post by nocturn on 2005-01-12
[QUOTE=Ste]There's a feature in this months LinuxFormat about backing up.
Bacula is capable of writing to DVD. Not sure how it's done however as I couldn't get an archiever to install as of yet.


[http://www.bacula.org/html-manual/index.html](http://www.bacula.org/html-manual/index.html) -- might be a bit more help.[/QUOTE]

I've set bacula up on my server at work, and it is great.
It does not directly support backing up to CD/DVD, but I have a workarround for this.

Create an archive pool for CD or DVD
Set the maximum size of volumes in that pool to 650 MB for CD's and 4.5 GB for DVD's.
Do not catalog files from this pool
Set retention to a short value that gives you enough time to write the medium.

Now you can run backups to that pool, and just write the files to a removable medium.
After burning, remove the volume from the console.
To import it back, copy archive file to the storage directory again (or symlink) and use bscan to import it into the catalog.
When done, remove it again.

---


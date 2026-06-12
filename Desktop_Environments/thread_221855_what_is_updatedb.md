---
title: "what is updatedb"
date: 2006-07-24
forum: Desktop Environments
---

### Post by linuksamiko on 2006-07-24
I have now clue what updatedb is for. I mean I wouldn't care if my harddisk would go crazy and my computer is getting (only a little) slow.
When I looked at all the running processes I found out that there is a parocesse called updatedb. Now I want to know what it is.

---

### Post by Lunar_Lamp on 2006-07-24
I'm not 100% sure, but as far as I know it basically builds a database of all your files so taht you can search for them more easily/faster using the 'slocate' [sic] command.

---

### Post by Thund3rstruck on 2006-07-24
updatedb is used to maintain the files listing for you. So when you search for a file such as fstab:

$locate fstab
/etc/fstab

updatedb should not run all the time, just when you or another program invokes it to update the new file/dir listings

---


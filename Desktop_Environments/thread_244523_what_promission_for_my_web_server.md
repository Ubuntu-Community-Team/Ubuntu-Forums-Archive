---
title: "what promission for my web server?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by doomstone on 2006-08-26
I have a server running apache2 on Ubuntu server.
but i have the problem that, my ftp users is "web" and apache uses "www-data" 
witch is fine.
i have set the owner of my www and subfolders to be owned by "web" and be part og "www-data" group.

It workes fine, but when i upload a new file do i have to do "chmod g+rwx /path/to/www/folder/"

So what is the smartest way i ca do this so i don't have to chmod evy time i upload files?

---


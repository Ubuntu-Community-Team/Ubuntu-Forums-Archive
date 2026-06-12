---
title: "(13)Permission denied: cannot read directory for multi:"
date: 2009-05-28
forum: General Help
---

### Post by rompstar on 2009-05-28
I keep seeing this error in my apache error.log, I did a search on it, but I am not sure what it means, I am not a pro on apache.

error is:    (13)Permission denied: cannot read directory for multi:

my apache web sites are n /home/raymond/www

raymond@dragonfly:~$ ls -ld /home /home/raymond /home/raymond/www
drwxr-xr-x  3 root    root    4096 2009-05-26 19:45 /home
drwxr-xr-x 74 raymond raymond 4096 2009-05-28 11:05 /home/raymond
drwx--x--x 18 raymond raymond 4096 2009-05-27 10:28 /home/raymond/www

If this is a permissions problem, please advise what I should chmod things to.

Thanks!

---


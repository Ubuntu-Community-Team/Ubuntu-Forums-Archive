---
title: "evince error after update"
date: 2010-07-07
forum: Desktop Environments
---

### Post by ite366 on 2010-07-07
Yesterday I updated some packages with the Update manager. A new version of evince was updated, too. However, no pdf, ps files can be opened by it after that.
Running from the command line, get error like:
"evince: symbol lookup error: evince: undefined symbol: ev_get_locale_dir"

I just wonder how to solve this. Or how to rollback to older version?
Thank you.

---

### Post by ite366 on 2010-07-07
Fixed.
Some GNOME document viewer library should also be updated at the same time. Otherwise it would cause error like above.

---

### Post by Telephonez_me on 2010-07-12
Thanks, that solved my problem.
-> libevdocument2 2.30.1-0ubuntu3 2.30.3-0ubuntu1
-> libevview2 2.30.1-0ubuntu3 2.30.3-0ubuntu1
according to /var/log/dpkg.log

---

### Post by Subespaciovectorial on 2010-08-09
Same problem. Those libs fix my problem too.
Thank you guys.

---

### Post by prakharbansal on 2010-09-27
Thanks for the Help ... 
It solved my prob as well... 

On my computer, the two packages were not installed initially.. so i had to run these two commands

apt-get install libevdocument2
apt-get install libevview2

and now evince is working for me.. 

Regards

---


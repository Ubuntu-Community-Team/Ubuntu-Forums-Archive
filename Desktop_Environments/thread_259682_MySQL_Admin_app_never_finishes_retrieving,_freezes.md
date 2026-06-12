---
title: "MySQL Admin app never finishes retrieving, freezes"
date: 2006-09-17
forum: Desktop Environments
---

### Post by locoHost on 2006-09-17
I startup MySQL Administrative tool, I click "User administration", the form displays (grey'd out, inactive) and I see the message at the bottom "Retieving data from MySQL" and "Please wait...". This is permanent. It never gets the data from MySQL and the form stays grey'd out. I have to force quit to close it. Any idea what's happening?

Thanks guys :-)

---

### Post by ilyaostr on 2006-09-17
i think that it has something to do with your hardware what aer your specs?

---

### Post by locoHost on 2006-09-17
Dell Inspiron 8100, PIII, 80GB HD, 512MB RAM, Drake 6.06

What would this have to do with it?

---

### Post by statue on 2006-09-18
I really don't think it has to do with your hardware as I have had the same problem with a completely different setup. As soon as I would click on user administration...the thing would freeze up. Happened everytime for me so I just started using phpmyadmin instead. It does all that mysql admin app does, it just is accessed through your browser. I recommend you do the same as I know of no fix for the mysql admin error...and yes, I do think it is a software issue, not a hardware one.

---

### Post by sbrydon on 2006-09-18
This post:

[http://forums.mysql.com/read.php?34,72959,78277#msg-78277](http://forums.mysql.com/read.php?34,72959,78277#msg-78277)

has a work around for this problem. The work around works on my machine here - Kubuntu 6.06.

I edited the Kmenu->System->MySQL Administrator entry and changed the command to be:

DEBUG_DONT_SPAWN_FETCHES=1 /usr/bin/mysql-admin

---

### Post by statue on 2006-09-18
Thanks for that, sbrydon.

---


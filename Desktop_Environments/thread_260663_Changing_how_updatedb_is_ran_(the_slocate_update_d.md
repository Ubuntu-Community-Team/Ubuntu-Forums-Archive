---
title: "Changing how updatedb is ran (the slocate update daemon)"
date: 2006-09-19
forum: Desktop Environments
---

### Post by nullmind on 2006-09-19
I have no problems with updatedb being ran to update my slocate database, I like this! I use slocate every 5 minutes and love how things are indexed. However, when I need things to be responsive it does annoy me. How can I change the nice value of the dameon so it will always start with a specific nice value?

---

### Post by monktbd on 2006-09-19
on my system slocate is called by cron.
the script calling it is located in cron.daily.

> #! /bin/sh
if [ -x /usr/bin/slocate ]
then
        if [ -f /etc/updatedb.conf ]
        then
                /usr/bin/updatedb
        else
                /usr/bin/updatedb -f proc
        fi
        chown root.slocate /var/lib/slocate/slocate.db
fi

chaning the commandlines in there to

> nice -n 19 /usr/bin/updatedb
> nice -n 19 /usr/bin/updatedb -f proc

should do the trick.

---


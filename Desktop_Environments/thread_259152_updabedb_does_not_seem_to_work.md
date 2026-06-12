---
title: "updabedb does not seem to work"
date: 2006-09-17
forum: Desktop Environments
---

### Post by jamesr on 2006-09-17
Hi,

I seem to have a problem with my Xubuntu installation and that is 
```
updatedb
or
sudo updatedb

```
does not generate file locatedb. Using the code```
locate locatedb
``` only finds > /usr/man/man5/locatedb.5.gzboth before and after the updatedb. The  updatedb command gives no errors

I have also tried to find the locatedb by using the command```
find / -name locatedb -print
```any suggestions greatfully received.

---

### Post by mitch.c on 2006-09-17
> **jamesr said:**
> I seem to have a problem with my Xubuntu installation and that is 
```
updatedb
or
sudo updatedb

```
does not generate file locatedb.
It shouldn't.. it generates /var/lib/slocate/slocate.db

---

### Post by jamesr on 2006-09-17
Hi,

Thanks for the quick reply, when did the change occur from locatedb to slocate.db? Also the location on my system was /etc/lib/slocate.db.

now to find why the auto update ie using cron or anacron does not work.

---

### Post by mitch.c on 2006-09-17
> **jamesr said:**
> when did the change occur from locatedb to slocate.db? Also the location on my system was /etc/lib/slocate.db.

I don't remember it being different. And although I couldn't find it in the man pages, I did do a quick google that seems to indicate that the default path to the db is /var/lib/slocate/slocate.db. The only way I can use a different db is:
```
sudo slocate -u -o /etc/lib/slocate.db
```

Is there something similar in cron or /etc/updatedb.conf that's creating it in /etc/lib? That seems like a strange place.

> **jamesr said:**
> now to find why the auto update ie using cron or anacron does not work.

What do you mean by "does not work"?

---

### Post by jamesr on 2006-09-18
Hi,

I have not changed anything with respect to operation of Updatedb in fact my googling indicated the the change occurred with version 4.0. This is the first time, that I have had problems with the updatedb  command in several years of operation with several distros, so I can only assume that the changes are in so way related to Xubuntu 6.06, because I do not believe that I had any problems with Ubuntu server nor my Kubuntu 5.04 system nor the Debian 3.1 on an Alpha.

No I have not changed the /etc/update.conf nor using the extended command line. I will be checking the update.conf file.

The problem with cron was that it was not running any commands at all, possibly traced, to a mangled crontab file (imported from another system.

Any way, the system is working  now, not checked for updated db file yet.

Thanks for your help much appreciated.

---


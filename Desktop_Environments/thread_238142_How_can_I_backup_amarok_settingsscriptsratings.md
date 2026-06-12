---
title: "How can I backup amarok settings/scripts/ratings?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Serguei_89 on 2006-08-17
Hello,

I'm planning to uninstall my ubuntu and install a fresh copy of Kubuntu. It's very important to me to preserve the state of amarok though. Album covers, ratings, scripts, settings, everything.

How would I go about doing that?

---

### Post by Lunar_Lamp on 2006-08-17
I'm fairly sure all the config stuff is located in ~/.kde/share/apps/amarok - so you just need to backup all the files in there.

---

### Post by Serguei_89 on 2006-08-17
That did not work. lol

I saved up the amarok folder where you said. Installed amarok in the new kubuntu, and then replaced its settings folder with the backed up one. Collection wasn't there and scripts were funny(4 enties for each script in the menu)

---

### Post by dwiel on 2007-07-17
what you want to do is backup that directory (its got settings etc.) and you want to backup the database. See [MySQL HowTo]("http://amarok.kde.org/wiki/MySQL_HowTo").  The database has your library of songs, score, etc

---

### Post by shift on 2007-09-16
alright sorry to dig up this thread but i have been workign on this for a few days and have had no luck.  Im trying to backup my amarok statistics database.  Currently I have the mysql database setup and working.  the problem comes when converting the sqlite database.  

I have been using this guide [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

when running this code
cd ~/.kde/share/apps/amarok && \
sqlite3 collection.db .dump | \ 
grep -v "BEGIN TRANSACTION;" | \
grep -v "COMMIT;" | \
perl -pe 's/INSERT INTO \"(.*)\" VALUES/INSERT INTO \1 VALUES/' | 
mysql -u root -p amarok

nothing really seems to happen.  Is there a specific order of running these commands? I tried running them all at once and lien by line.  nothing happenes either way.   

I did just instlal sqlite3 so that commad does work.  any ideas?

Thanks a bunch.

---


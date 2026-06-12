---
title: "Offsite Back-up solutions"
date: 2009-03-27
forum: General Help
---

### Post by makaymurray on 2009-03-27
Hey linux users out there.

Im trying to find a simple and easy (cost is no object) back-up solution to transfer and update roughly 10TB of data between buildings. 

Now I know 10TB is a whole bunch of data and would take about a year or two to transfer over the internet. However the system im backing up only generates maybe 100mb of data a day. so for the initial back-up i plan just to bring several large drive enclosures and sync them with my server here, then take them off site and set up the back-up software to just save the incrimental changes. note: bit-per-bit would be preferable because most files are 100mb in size and we often just change 1kb of data. it would be un economical to do complete file back-ups.

Theres my speil. Any help will be apprechiated.

---

### Post by ImpelGD on 2009-03-27
Linux nub here, but have you looked into rsync?

---

### Post by LowSky on 2009-03-27
If cost is no option and this is for a company, get a T1 or faster point to point internet connection.

Look into a company like Barracuda (My company uses them for our Disaster Recovery Site)
[http://www.barracudanetworks.com/ns/?a=google-backup_offiste&t=bbs&gclid=CNqStM6QxJkCFRJ4xgodOkcSvA&L=en](http://www.barracudanetworks.com/ns/?a=google-backup_offiste&t=bbs&gclid=CNqStM6QxJkCFRJ4xgodOkcSvA&L=en)

transfers 10TB may take a few days but it wont be too bad, but then again if you youthem all beofre you even build the other site then its easier

---

### Post by James_Lochhead on 2009-03-27
Yea rsync via ssh would be good if you had a net connection with a reasonable upload speed.

You would just simply connect to the server via ssh. Then run the rsync command, this is the one I use to sync my music to my blackberry:

rsync -r -v --del /home/user/Music /media/Blackberry/Music/

You would simply replace the the first link with the one on your hard drive and the second link with the external backup.

---

### Post by rjl6591 on 2009-03-27
Duplicity is an off-site backup package that uses rsync, ssh and openpgp to do secure off-site backups. It may be worth a look. There are Ubuntu packages of it.

[http://duplicity.nongnu.org/]("http://duplicity.nongnu.org/")

---


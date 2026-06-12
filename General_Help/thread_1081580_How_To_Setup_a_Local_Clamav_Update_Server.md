---
title: "How To Setup a Local Clamav Update Server"
date: 2009-02-26
forum: General Help
---

### Post by bigmeanogre on 2009-02-26
1.Install base Ubuntu Server (we use 8.04 LTS)

2.Choose the Openssh and LAMP server options

3.Enable the backports reposistory in /etc/apt/sources.list, to get the latest client

4.Change the Document Root for Apache to /var/lib/clamav/

5.Create a daily update script to get the main.cvd and daily.cvd file
I called mine clamup.sh, and below is a listing of it's content:

[I]#!/bin/sh
cd /tmp
wget [http://database.clamav.net/daily.cvd](http://database.clamav.net/daily.cvd)
wget [http://database.clamav.net/main.cvd](http://database.clamav.net/main.cvd)
mv main.cvd /var/lib/clamav/
mv daily.cvd /var/lib/clamav/
apt-get update && apt-get upgrade -y && /etc/init.d/clamav-freshclam restart
[/I]
	    
The last line updates the system, and restarts freshclam. 
If you don't want automatic updates, you can replace that line with:
[I]
/etc/init.d/clamav-freshclam restart[/I]

6. Create a script to update the 'thru the day' virus updates
   I called mine clamsubver.sh, and below is the listing of it's content:

[I]#!/bin/sh
cd /tmp
ver=`host -t txt current.cvd.clamav.net > /tmp/version.txt && awk  -F":" '{print $3}' /tmp/version.txt`
dl="daily-$ver.cdiff"
wget http://database.clamav.net/$dl
mv /tmp/$dl /var/lib/clamav/
[/I]

This script checks the Clam DNS record for latest version, and then downloads it.

7.setup cron to run both scripts. Mine looks like this:

[I]59 11 * * * /sbin/clamup.sh
15 * * * * /sbin/clamsubver.sh
[/I]

8.Now point your clients to update from your server, and watch it work.:guitar:

All connections (or lack thereof) can be tracked in the server's apache access.log in /var/log/apache2

---


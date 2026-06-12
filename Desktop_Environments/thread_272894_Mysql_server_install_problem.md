---
title: "Mysql server install problem"
date: 2006-10-07
forum: Desktop Environments
---

### Post by sirhobbit on 2006-10-07
I have been trying to install mysql server, when I enter 
apt-get install mysql-server I get the following error:

"The following packages have unmet dependencies:
mysql-server: Depends: mysql-client (>= 4.0.24-10ubuntu2.3)
E: Broken Packages"

So I tried to install mysql-client and got the same error for libreadline4 so I tried to install that package but it tells me that it is going to uninstall about every package on the system to do so.

Help!

---

### Post by rogier.de.groot on 2006-10-07
Which repositories do you have enabled? Could you try to install a specific version of mysql (eg mysql-server-5.0) ?

---

### Post by sirhobbit on 2006-10-07
My sources list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

---

### Post by rogier.de.groot on 2006-10-07
Hmm... I'd recommend backuping up apt's source list, change everything back to default (eg. breezy, updates & security - main & restricted) and try sudo apt-get update && sudo apt-get install mysql-server && sudo apt-get clean after that. Change back the old source list afterwards. That should work... I guess...

---

### Post by sirhobbit on 2006-10-07
Thanks Rogier!

That seems to work as the server is now downloading the required packages. I'll keep it on the default package list until I need extra packages (not likely)

Thanks again!

---

### Post by rogier.de.groot on 2006-10-07
Cheers :)
For the record, I always keep my source list on the default repositories, but with universe & multiverse enabled too... Many usefull things in those parts... BTW, why Breezy and not Dapper? Just wondering...

---

### Post by stansaraczewski on 2006-10-07
Which repository will I find Apollon in ? Seems that //security.ubuntu.com dapper-security/restricted Sources is hung up at the moment - 'waiting for headers'... anyplace else I can look ?

---

### Post by stansaraczewski on 2006-10-07
Wrong thread - sorry... :???:

---


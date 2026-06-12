---
title: "mysql_config question"
date: 2007-10-11
forum: Desktop Environments
---

### Post by radioraheem on 2007-10-11
I have a desktop machine that I need to run a perl script on.  This script requires the DBD::mysql perl module which I am having problems installing because it cannot locate mysql_config.

I installed the following via apt-get and they do not appear to have setup a mysql_config anywhere:

libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-common mysql-server-4.1 mysql-server-5.0

Does anyone know what I need to install?  It's a fairly simple perl script, I just need to get the right modules installed.

Many thanks for any help!

:)

---

### Post by radioraheem on 2007-10-12
anybody?  Sorry to bump this post, but this seems like it should be a pretty simple question.

---

### Post by zaziork on 2007-11-03
Just run into the same issue whilst compiling something. 

You need to install libmysqlclient[YOUR MYSQL VERSION NUMBER]-dev. To install from the repos, make sure your mysql version is the same as the latest in the repositories, then:

To find current version number:

> sudo aptitude search libmysqlclient

You'll see a package with number at after libmysqlclient. For example, at time of writing, it's 15, so it looks like this: libmysqlclient15-dev.

Then:

> sudo apt-get install libmysqlclient15-dev

That should install mysql_config for you. Hope this helps.

---


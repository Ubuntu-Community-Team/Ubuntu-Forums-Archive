---
title: "amaroK Web Frontend"
date: 2005-10-05
forum: Desktop Environments
---

### Post by beefsprocket on 2005-10-05
Has anyone successfully setup the "[amaroK Web Frontend]("http://www.kde-apps.org/content/show.php?content=25398")" script from [kde-apps.org]("http://www.kde-apps.org")? I'm having a difficult time with it. The error I get (regardless of what I name the directory) is as follows:

> **Fatal error**:  Call to undefined function:  mysql_connect() in **/var/www/apache2-default/amaroK frontend/inc/globals.inc.php** on line **87**

The offending line in globals.inc.php is as follows:

> mysql_connect($dbinfo['host'], $dbinfo['user'], $dbinfo['pass']) or die(mysql_error());

I've tried numerous configurations with apache2 and php(4 and 5). Anyone have a definitive way to avoid the error and let me listen to my music wherever I may happen to end up?

---

### Post by djgrandmarquis on 2006-09-30
Have you installed the -dev package for the libmysqlclient package? Looks like that might be it.

I've installed libmysqlclient15off and libmysqlclient15-dev.

---


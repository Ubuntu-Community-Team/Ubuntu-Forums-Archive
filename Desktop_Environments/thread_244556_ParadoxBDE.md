---
title: "Paradox/BDE"
date: 2006-08-26
forum: Desktop Environments
---

### Post by phossal on 2006-08-26
I own a copy of Corel Paradox 9 for Windows, but I'm unable to get it running under wine. Other than installing wine, I did nothing to configure it. I'm sure that's why I'm having trouble installing software.

I need to be able to execute sql statements against Paradox tables from my Ubuntu (Dapper) box. Is there a different way to do this?

---

### Post by LKRaider on 2006-08-26
Checking the winehq app database for Paradox:
[http://appdb.winehq.org/appview.php?iAppId=1324](http://appdb.winehq.org/appview.php?iAppId=1324)

Seems version 7 works - somewhat. Version 8 not much, and version 11 there is no report :/ 
Version 9 is not even mentioned.
I found a [page]("http://www.prestwood.com/community/paradox/") mentioning this tho: "Corel released Paradox 9 for Linux using the wine emulator."

You could also try running it under VMWare.

Another idea is to convert the Paradox database into another format (like MySQL) and using it natively under linux.


For reading Paradox db's, check pxlib1 (on the repos) and the site: [http://pxlib.sourceforge.net/](http://pxlib.sourceforge.net/)
The tool pxview can convert Paradox DB files. ( ex: "*pxview -s -o MyDB.sql MyDB.DB*"  will convert the paradox db to sql format)

Also, checking pxlib1 dependent packages, gnumeric-plugins-extra is listed as one of them, so probably Gnumeric can be setup to access the Paradox DB's somehow.


Oh, and checkout Knoda, as it is also listed in pxlib website and support Paradox db's.
[http://www.knoda.org/](http://www.knoda.org/)
[http://www.kde-apps.org/content/show.php?content=9808](http://www.kde-apps.org/content/show.php?content=9808)

---


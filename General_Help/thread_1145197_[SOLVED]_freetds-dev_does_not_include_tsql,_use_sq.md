---
title: "[SOLVED] freetds-dev does not include tsql, use sqsh."
date: 2009-05-01
forum: General Help
---

### Post by coldnebo on 2009-05-01
If you are connecting to Microsoft SQL Server and using the freetds-dev package, you have probably seen docs that tell you to use the tsql utility to test the connection after installation, e.g. the official user guide:

[http://www.freetds.org/userguide/confirminstall.htm](http://www.freetds.org/userguide/confirminstall.htm)

However, deb maintainers have removed that utility from the freetds-dev package -- it seems that too many people were tempted to use tsql for more than just testing, so they removed it completely.  This means if you install freetds-dev you will not get tsql.  This thread explains the rational and encourages users to use sqsh instead:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=196000](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=196000)

You can get sqsh via:

```
% sudo apt-get install sqsh
```I think there are good reasons for what the deb maintainers did, but I wish they could have contacted freetds to update their docs with some kind of warning.  It would have saved a lot of grief.


Note: The previous ubuntu forum hit for "freetds tsql" was out of date and unanswered for 2 years:

[http://ubuntuforums.org/showthread.php?t=252606&highlight=freetds+tsql](http://ubuntuforums.org/showthread.php?t=252606&highlight=freetds+tsql)

I hope this saves new people some grief while trying to follow the official docs.

---


---
title: "Tracker problems with sparql"
date: 2011-01-23
forum: Desktop Environments
---

### Post by Jim_Hope on 2011-01-23
Dear All,

Sometimes Ubuntu 10.10 takes five minuts to load from the log-in screen; about five times as long as 10.04 (I am running an X61 tablet with 4GB RAM). When I look in .xsessions, I see the following error repeated:

(tracker-miner-fs:2837): Tracker-CRITICAL **: Could not execute sparql: Unable to insert multiple values for subject `urn:software-category:%2Fusr%2Fshare%2Fdesktop-directories%2Fkde-edu-miscellaneous.directory' and single valued property `nfo:fileLastModified' (old_value: '<untransformable>', new value: '<untransformable>')

SHOULD NEVER HAPPEN
SHOULD NEVER HAPPEN
SHOULD NEVER HAPPEN
SHOULD NEVER HAPPEN

The "should never happen" then repeats ominously down the screen, followed by 

(nautilus:2813): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

I have done forum searches and google searches, but cannot find anything out about this error, or how to fix it.

Any help appreciated,

Jim.

---


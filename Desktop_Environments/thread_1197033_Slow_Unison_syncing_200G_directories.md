---
title: "Slow Unison syncing 200G directories"
date: 2009-06-25
forum: Desktop Environments
---

### Post by creatron on 2009-06-25
Unison is busy, (and it only reached 34%) after three days!!, syncing 200Gbyte. The gui screen updates is also every n seconds where n is >>> 1sec. Sometimes it just does not refresh the gui screen for minits at all. It does however works great for small directories. My setup is as follows:
(repository.prf)
root = /external/server/repository
root = /nfs/server/repository
force= /external/server/repository
# Ignore certain directories and files
ignore = Path db
# Helps out a lot on Windows
#fastcheck = true
# Don't synchronize permission bits
perms = 0
# Place new files at the top of the list
sortnewfirst = true
ignore = Name *.bak
ignore = Name *.BAK
ignore = Name *.log
ignore = Name *.LOG
ignore = Name *.rel
# Log actions
log = true
logfile = /home/gerrie/.unison/repository.log

The "remote" directory is mounted nfs. Unison is suppose to be slow the first time, but is this normal for 200G's ?

Can I stop the process now without corrupting my system ?

Regards
Gerrie

---


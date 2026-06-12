---
title: "can't create help index using htdig"
date: 2005-05-01
forum: Desktop Environments
---

### Post by gaboo on 2005-05-01
I'm trying to create the help index in khelpcenter bue I keep having this error :
```
INDEXDIR: /home/gaboo/.kde/share/apps/khelpcenter/index/
FINDCMD: find /usr/share/doc/HTML/en/ -name index.docbook
Creating index for 'kde_application_manuals'
Warning: unknown locale!

New server: home, 80
0:0:0:file://home/gaboo/.kde/share/apps/khelpcenter/index/kde_application_manuals.tmp/index.html:  size = 0
htdig: Run complete
htdig: 1 server seen:
htdig:     home:80 1 document
DB2 problem...: missing or empty key value specified
Finished successfully.
```

Any ideas ?

---

### Post by casfindad on 2005-12-29
Hopefully you've worked this out already, but if not...

Install htdig using adept or synaptic, then try building your search index again. This worked for me.

It took far, far too long for me to figure out, however. ;-)

---

### Post by Maciek on 2006-01-17
[QUOTE=casfindad]Hopefully you've worked this out already, but if not...

Install htdig using adept or synaptic, then try building your search index again. This worked for me.

It took far, far too long for me to figure out, however. ;-)[/QUOTE]

Actually you get the output that the original poster shows only if you already installed "htdig".  I'm having the same problem.  I installed "htdig" and rebuilt the index.  The Details show some warnings about a host called "home" (probably some silly default value somewhere), and about only finding 1 document.  Doing searches through the now built Aplication Manual database does not find anything, even when searching for words one *knows* are in one of the manuals.  Something is still broken.

---


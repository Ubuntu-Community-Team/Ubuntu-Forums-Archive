---
title: "How to schedule a java program in cron"
date: 2008-09-07
forum: Desktop Environments
---

### Post by mister_p_1998 on 2008-09-07
Hi guys,
Im trying to get TED (The torrent search tool) to start in cron. Its a java program which runs from the commandline like this: java -jar /home/steve/Ted/ted.jar

Im trying to schedule it it cron with this entry:
# Ted
00 02 * * 1,2,3,4,5 export DISPLAY=:0 && /usr/bin/java -jar /home/steve/Ted/ted.jar

But nothing goes off, is it a java problem?
TIA
Steve

---


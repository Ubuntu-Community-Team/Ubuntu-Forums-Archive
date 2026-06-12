---
title: "Cannot Kill Process - tried everything I know!"
date: 2009-02-03
forum: General Help
---

### Post by Neural oD on 2009-02-03
Hi - I have a cdrecord process running that seems to have gone bad - my cd-rom is running overtime! I'm trying to kill the process, but nothing seems to work! I've tried - using root account by the way: kill -9 xxxxx  also tried pkill xxxxx and kill -KILL xxxxx

what gives?

---

### Post by binbash on 2009-02-03
try with fuser -km /mnt/cdrom etc

---

### Post by Neural oD on 2009-02-03
didn't work - but thanks for that - I learnt of a new prog!

Had to restart my machine eventually as nothing seemed to work. Weird that - I always complained that windows didn't allow you to do things that you wanted - now for the first time I've not been able to terminate a process!

---


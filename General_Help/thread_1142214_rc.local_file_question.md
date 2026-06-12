---
title: "rc.local file question"
date: 2009-04-29
forum: General Help
---

### Post by Sapfeer on 2009-04-29
Hello

Recently I've upgraded to 9.04 and I putted the following code in my **rc.local** file:
```
echo Calling internet... > /home/user/rc.local.log
echo Using pon >> /home/user/rc.local.log
/usr/bin/pon internet

```But log after login log file looks like his: 
```
[ user@lenovo-y510ka Wed 29 Apr 2009 08:12:26 AM MSD ]
/home/user # cat rc.local.log 
Calling internet...
```I don't understand what I did wrong...

---


---
title: "Restoring tbird mail"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Dai-Galean on 2006-06-23
Well I found this very frustrating to say the least. 

First I did what it says here at the mozilla site
[http://www.mozilla.org/support/thunderbird/profile#move](http://www.mozilla.org/support/thunderbird/profile#move)
then when it came time to move the xxxxxxxx.default dir back I get this from the  program

*There is a copy of thunderbird already running, please close it down or reboot your computer*

Well for one there is no copy of tbird running.

Is there a way to backup tbird mail, settings, etc or can anyone suggest a email programme that does this?

---

### Post by jrattner on 2006-06-23
Type:
```
ps auxw|grep -i "thunderbird"
```

That should find the running process, then just kill the PID.  Thunderbird is a great mail client which WILL allow you to transfer, back up and restore e-mail settings.

---


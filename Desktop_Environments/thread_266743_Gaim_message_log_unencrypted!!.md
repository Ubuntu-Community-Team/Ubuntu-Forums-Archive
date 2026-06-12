---
title: "Gaim message log unencrypted??!!"
date: 2006-09-27
forum: Desktop Environments
---

### Post by DC@DR on 2006-09-27
Hi folks,

Today I just found out that: Since I enabled the message logging feature in Gaim, I could be able to view the message logs (~/.gaim/logs/yahoo/your_account/)in PLAIN TEXT!!!. Why shouldn't those personal logs be encrypted?? Can any1 tell me how to keep those logs out of curious eyes? Many thanks :)

---

### Post by wombat20 on 2006-09-27
Most chat programs do not encrypt their log sessions.  In fact I can't think of one which does.

I think that by default these files are not readable to anyone not logged in as you.  If you right-click on the files (or for that matter the ~/.gaim folder) and select Permissions, you should see that Others does not have read access to them.

Of course anyone using your machine whilst logged in as you can read them.

---

### Post by powder on 2006-09-27
Just remove permissions on the log files for everyone but yourself. ;)

```
chmod go= logfile.txt
```

---

### Post by DC@DR on 2006-09-28
But I think at least it should be encoded/encrypted or kind of, and the idea should be only when you're logged in to that chat account, you'll be able to view those logs, otherwise, those logs should be kept encoded/encrypted, not as in plain text format as they are now, I just feel kinda weird when Gaim doesn't protect its logs properly...Is there any plugins for Gaim or Gaim 2.0 that is gonna deal with this particular issue? :)

---

### Post by lamego on 2006-09-28
> But I think at least it should be encoded/encrypted or kind of, and the idea should be only when you're logged in to that chat account, you'll be able to view those logs, otherwise, those logs should be kept encoded/encrypted, not as in plain text format as they are now, I just feel kinda weird when Gaim doesn't protect its logs properly...Is there any plugins for Gaim or Gaim 2.0 that is gonna deal with this particular issue?
The general sense for "log files" is a text file that logs all the activity and which can be used for further processing, meaning most people may want to look their logs on "gedit", or may want to look on them with "grep" or they can have a statistical program which parses the logs, that is the default use of log files, usual log files are not encrypted.
So your problem seems to be the lack of an "encrypted" log plugin, I guess you will need to submit a request to the gaim team.

---


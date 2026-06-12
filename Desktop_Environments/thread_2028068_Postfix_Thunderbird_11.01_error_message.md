---
title: "Postfix Thunderbird 11.01 error message"
date: 2012-07-17
forum: Desktop Environments
---

### Post by skaramanger on 2012-07-17
Greetings,

Awhile back I was tearing what little hair I have left out trying to figure out what is the issue with postfix and thunderbird. Or is it just TB?  I'll post examples in a moment, I just what to let all know that I have been perusing these forums for some answers so now I'm asking for the communities help.

```
Jul 17 14:32:08 my-unit postfix/pickup[8215]: D1992ED0F3: uid=1000 from=<Iuser>
Jul 17 14:32:08 my-unit postfix/cleanup[9839]: D1992ED0F3: message-id=<20120717183208.D1992ED0F3@myhostname>
Jul 17 14:32:09 My-Unit postfix/qmgr[8216]: D1992ED0F3: from=<Iuser@myhostname.local>, size=350, nrcpt=1 (queue active)
Jul 17 14:32:09 My-Unit postfix/local[9841]: D1992ED0F3: to=<Iuser@myhostname>, orig_to=<root@myhostname>, relay=local, delay=0.28, delays=0.21/0/0/0.08, dsn=5.2.0, status=bounced (cannot update mailbox /home/Iuser//home/Iuser/.thunderbird/oyqponwh.default/Mail/localhost-2 for user Iuser. unable to create lock file /home/Iuser//home/Iuser/.thunderbird/oyqponwh.default/Mail/localhost-2.lock: No such file or directory)
Jul 17 14:32:09 myhostname postfix/cleanup[9839]: 2389FED0F6: message-id=<20120717183209.2389FED0F6@tz-desktop>
Jul 17 14:32:09 myhostname postfix/bounce[9842]: D1992ED0F3: sender non-delivery notification: 2389FED0F6
Jul 17 14:32:09 myhostname postfix/qmgr[8216]: 2389FED0F6: from=<>, size=2589, nrcpt=1 (queue active)
Jul 17 14:32:09 myhostname postfix/local[9841]: 2389FED0F6: to=<Iuser@myhostname>, orig_to=Iuser@myhostname.local>, relay=local, delay=0.31, delays=0.19/0/0/0.12, dsn=5.2.0, status=bounced (cannot update mailbox /home/Iuser//home/Iuser/.thunderbird/oyqponwh.default/Mail/localhost-2 for user Iuser. unable to create lock file /home/Iuser//home/Iuser/.thunderbird/oyqponwh.default/Mail/localhost-2.lock: No such file or directory)
Jul 17 14:32:09 myhostname postfix/qmgr[8216]: D1992ED0F3: removed
Jul 17 14:32:09 myhostname postfix/qmgr[8216]: 2389FED0F6: removed

```

I do note in the above code an error in the path to where the lock file is supposed to be deposited.  Apparently, Thunderbird gets confused and duplicates the path to my home directory.

Is there a thunderbird config file to search for that I can manipulate directly to allow me to receive system mail?

Thanks In Advance,

Skaramanger

---

### Post by skaramanger on 2012-07-18
Any chance of a bump?

---


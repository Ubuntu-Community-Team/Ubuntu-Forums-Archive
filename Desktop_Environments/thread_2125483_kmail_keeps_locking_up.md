---
title: "kmail keeps locking up"
date: 2013-03-14
forum: Desktop Environments
---

### Post by dargaud on 2013-03-14
Hello all,
I've had the problem of kmail locking up every once in a while for years, but it's happened 3 times in the last 3 days. And it's not just a case of closing it and reopening it: there are sub-processes which, if killed, make it so that kmail won't work until the next reboot.
So what happens ? It checks for mail on my pop3 accounts and it never finishes. I can keep using it in the meanwhile but no new messages come in.

Unless someone can **explain how to restart kmail properly**, I have to reboot the system, which I am loathe to do (it's a server for a lot of things).
```
$ ps faux | grep mail
user   2865  0.0  0.6 340156 48536 ?        Sl   Mar13   0:02  \_ /usr/bin/akonadi_agent_launcher akonadi_maildir_resource akonadi_maildir_resource_0
user   2866  0.0  0.3 339660 24676 ?        S    Mar13   0:00  \_ /usr/bin/akonadi_maildispatcher_agent --identifier akonadi_maildispatcher_agent
user   2867  0.0  0.6 625308 48880 ?        Sl   Mar13   0:01  \_ /usr/bin/akonadi_mailfilter_agent --identifier akonadi_mailfilter_agent
user   3451  3.0  1.4 2158064 115224 ?      Sl   Mar13  27:01 /usr/bin/kmail -session 10e5cedc67000136319936300000026520023_1363201973_899610

```

---

### Post by hainen on 2013-03-14
try with <akonadictl restart/stop/start>

It exist a graphical utility "Akonadi Configuaration" that should do the same thing, or add the akonadi tray icon.

---


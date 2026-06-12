---
title: "Thunderbird does not start after removing indexes"
date: 2012-07-14
forum: Desktop Environments
---

### Post by manolomanolo on 2012-07-14
Hi to all.

I have been experiencing some problems with Thunderbird, so I thought it was a good idea to force TB rebuinding indexes.
So, I tried removing the index related to the "Sent" folder, that was the folder in trouble. I restarted TB and the "Sent" folder was completely fixed: all the problems were solved.
So, I thought it could have been a good idea forcing the rebuild of all the indexes of the other folders.
In detail, I moved to trash all the *.msf files contained into mt TB folder.
After that, TB does not want to start anymore: when I launch it it crashes almost immediately.

When launching it by terminal I only get the following message:
```
ReminderFox  clh(1)  {rmFx_cmdLine: [xpconnect wrapped nsICommandLine]}
```
Reminderfox is an addon that I installed some months ago, never had problems with it, no recent updates to it. So, I don't think it could be the cause of the problem.

Reinstalling TB did not work.
Purging and reinstalling did not work.

Running TB as root made TB start, but of course no email account was configured since I use to run TB as normal user.

Actually the solution come while asking for help on irc://moznet/%23thunderbird
The user d-tech suggested me to run TB in safe mode (open a terminal and run ```
 thunderbird -safe-mode
```).
A window will appear asking you to permanently apply some modification. I choose NOT to apply any modification when not in safe mode.
So, TB started regularry but with any addon disabled: it just started with defauld configuration. That maybe give TB the time to reestablish itself after removing all indexes (maybe any conflict with previously installed addons?).

Hope it helps.
Have a nice life on Gnu/Linux world!

---


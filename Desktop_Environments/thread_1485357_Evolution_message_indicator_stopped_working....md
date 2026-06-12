---
title: "Evolution message indicator stopped working..."
date: 2010-05-16
forum: Desktop Environments
---

### Post by x-shaney-x on 2010-05-16
Not sure exactly when this happened.
I noticed (and posted here) several days ago that notification SOUNDS had stopped working but now the indicator isn't working at all with evolution.

I get pop-up OSD notification things saying I have a new message but the indicator doesn't change to green and there is no entry for new messages or message counter in the menu, though the arrow is there to indicate evolution is running.

---

### Post by x-shaney-x on 2010-05-16
Ok, now the whole email entry in the messaging menu keeps randomly vanishing.
When I launch Evo manually the entry returns but still not working indicator-wise.

Also, Evo is randomly crashing (more than usual anyway).

---

### Post by x-shaney-x on 2010-05-17
Ok so I narrowed down this problem.
After restoring Evolution from a backup, everything was working normally again.
The only thing I had done since the backup was add another account and add filters so messages to that account would go into a second inbox.

So after restoring I added the account again and everything was still working.
Added the filter again - 1 rule for recipient and a rule to move messages to the second inbox.

Restarted Evo and the indicator refused to work again.
Not only that but I have been experiencing the random crashes again.

So am I to take it Evo simply does not like multiple inboxes?
Seems to me (from past experience as well) anything remotely different from a default setup causes Evolution to bug out completely.

Seriously, this app has been gnome default for so many years now, how many more years is it going to take to make it stable?

---

### Post by kevinanchi on 2010-06-21
Yes thats correct as i have configured 5 mail ids and none of them works and the Evo always crashes is there any permanent fix for the same..........

---

### Post by Micha401 on 2010-06-21
Yes, Evolution is - sad enough - still buggy and unstable. But you can run it with some precautions:
If something is very wrong, you can do this to reset it without loosing data:
1) Don't backup, but **export** all your compartments (mail, calendar, contacts &c.).
2) Uninstall Evolution and all additional components with purge
3) rm -rf .evolution
4) Important: In the gnome configuration database unset all /apps/evolution keys recursively
5) Reinstall Evolution and all needed components
6) Import data back.
Of course, you have to set up again mail accounts and mail filters, signatures. But the important things are back in an running prog.
BTW, I updated Evo this way to 2.30 in Ubuntu 10.4 amd64. My impression of 2.30 is much better then of 2.28. Unfortunately, this latest Evo version is not supported by Ubuntu, but there is a ppa around.
Evolution installed, it is worth to have a look into said /apps/evolution keys. You will find there settings unavailable or hidden in the program itself.
BTW, I use Evolution always sitting in the system tray. Doing so Evolutions checks itself for new mails and is at hand without lingering around as a panel button.
Considering the instability of Evo, I re-spawn this process and do a daily cron backup of Evo. If someone like, please find the scripts on my website.

---


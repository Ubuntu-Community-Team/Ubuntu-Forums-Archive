---
title: "Editing /etc/crontab"
date: 2006-08-06
forum: Desktop Environments
---

### Post by firebadger on 2006-08-06
Hi,

I would like to modify the time that my cron.daily and cron.weekly tasks run at.  I've tried sudo [FONT="Courier New"]crontab -e[/FONT], but I only get an empty file to edit.  I've also tried [FONT="Courier New"]sudo su -[/FONT] to become root and then [FONT="Courier New"]crontab -e[/FONT] but still it's an empty file.

What should I do?

---

### Post by 5-HT on 2006-08-06
You could edit /etc/crontab to change the times cron.daily and cron.weekly are run. Best to make a backup before hand.

---

### Post by firebadger on 2006-08-06
I know, my question is why does the command...
[FONT="Courier New"]sudo crontab -e[/FONT]
give me an empty file to edit rather than the contents of /etc/crontab?

---

### Post by 5-HT on 2006-08-06
> **firebadger said:**
> I know, my question is why does the command...
[FONT=Courier New]sudo crontab -e[/FONT]
give me an empty file to edit rather than the contents of /etc/crontab?

Because they are not the same things.
The system-wide crontab of /etc/crontab handles anything in /etc/cron.{daily, weekly, montly}. User crontabs are manipulated using the crontab command. 
You need to edit /etc/crontab by hand for the system-wide crontabs as my previous post said.
Alternatively, you could put the jobs in either your user's or root's crontab using the crontab command and set them up exactly as you want without having to modify cron.{daily, weekly, monthly}.

---

### Post by firebadger on 2006-08-06
Ah, I thought the /etc/crontab file was effectively the root users crontab.  Thanks!

---


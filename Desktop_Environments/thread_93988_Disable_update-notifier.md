---
title: "Disable update-notifier"
date: 2005-11-23
forum: Desktop Environments
---

### Post by senseiwa on 2005-11-23
Hi!

I have some workstations using ubuntu 5.04 and 5.10. I'd really like to disable permanently the update-notifier, that icon popping out every time an update is out.

Under 5.04 there's no disable, I always have it on... can anyone help me? :D

I know, it's probably something stupid...

---

### Post by Xian on 2005-11-23
Try removing the package:

```
$ sudo apt-get remove update-notifier
```

---

### Post by senseiwa on 2005-11-23
[QUOTE=Xian]Try removing the package:

```
$ sudo apt-get remove update-notifier
```[/QUOTE]

Unfortunately it wants to remove ubuntu-desktop... and I want to disable or remove just the update manager...

---

### Post by quietglow on 2005-11-23
Can't you right click and unselect "show notifications?"

---

### Post by Bou on 2005-11-23
Ubuntu desktop is just a collection of packages, it's OK to uninstall it.

---

### Post by senseiwa on 2005-11-23
[QUOTE=Bou]Ubuntu desktop is just a collection of packages, it's OK to uninstall it.[/QUOTE]

Thanks! This solved my problem :)

---

### Post by Sepero on 2007-09-11
This thread is pretty old, but I just wanted to point out a different solution to the problem.

If you want to disable update notifier for one user and not others:
System -> Preferences -> Sessions
Startup Programs (tab)
[uncheck] Update Notifier
Close

---

### Post by dlublink on 2008-06-02
> **Sepero said:**
> This thread is pretty old, but I just wanted to point out a different solution to the problem.

If you want to disable update notifier for one user and not others:
System -> Preferences -> Sessions
Startup Programs (tab)
[uncheck] Update Notifier
Close

I notice that in xubuntu 8.04, even if it's unchecked update-notifier loads anyway ( I see it in top )

---

### Post by Cheesehead on 2008-07-18
On Xubuntu 8.04 I removed the update-notifier package (nothing depends on it any more). To remove it, you can use Synaptic or the command line:
sudo apt-get remove update-notifier

To replace it, I used a cron job that e-mails me a weekly reminder every Sunday.
To edit your crontab, use crontab -e
Add the following line: ```
40 7 * * sun /usr/bin/nail -s "Reminder Bot: Run Update-Manager" [email]me@example.com[/email] >/dev/null
```

Explanation:
40 7 * * sun      - cron's time commands (see Intro to Cron at [http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)).
/usr/bin/nail -s  - send an e-mail message from the nail application.
"Reminder Bot: Run Update-Manager"    - e-mail subject
[email]me@example.com[/email]    - my destination e-mail address
>/dev/null        - cron's internal e-mail generator (I don't use it)

Note, this uses the nail package, which I use to create automated e-mails (not spam) across the various machines on my network.
Nail is available in Synaptic, or use: sudo apt-get install nail

---


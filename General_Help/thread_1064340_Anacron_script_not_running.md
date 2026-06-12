---
title: "Anacron script not running"
date: 2009-02-08
forum: General Help
---

### Post by MarshyTheKid on 2009-02-08
I have a backup script that I want to have ran everyday. It is sitting in /etc/cron.daily

script(Named backup and is executable.)
```
#!/bin/bash
dpkg --get-selections > ~/Backup/packages
cp /etc/apt/sources.list ~/Backup/sources.list.backup
```
It runs fine when I run it in terminal, but doesn't run with the other scripts.

/etc/anacrontab:
```
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly
```

Any clue why its not running or putting the files in my Backup folder?

---

### Post by dcstar on 2009-02-09
> **MarshyTheKid said:**
> I have a backup script that I want to have ran everyday. It is sitting in /etc/cron.daily

script(Named backup and is executable.)
```
#!/bin/bash
dpkg --get-selections > ~/Backup/packages
cp /etc/apt/sources.list ~/Backup/sources.list.backup
```
It runs fine when I run it in terminal, but doesn't run with the other scripts.
.........
Any clue why its not running or putting the files in my Backup folder?

A cron environment is NOT a user environment - cron does not know what "~" means.

Put in explicit paths for everything.

---

### Post by MarshyTheKid on 2009-02-09
Thanks. I'll give that a try. How can I force it to run?

---

### Post by MarshyTheKid on 2009-02-09
> **dcstar said:**
> A cron environment is NOT a user environment - cron does not know what "~" means.

Put in explicit paths for everything.

That fixed it! Thank you

---

### Post by geirha on 2009-02-09
> **dcstar said:**
> A cron environment is NOT a user environment - cron does not know what "~" means.

Not entirely true. Anacron runs the script with whichever shell is in the sh-bang (#!/bin/bash), and bash understands the "~" and replaces it. However, since anacron is run as root, the bash it spawns will also run as root, and ~ will be expanded to /root/ instead of your user's homedir, as it would if you ran it with sudo in a regular terminal.

Also, install the [mailx](apt:mailx) package. If you do that, cron will send you mail when a cronjob fails. You read such mail with the mail command:
```
mail
# or
sudo mail

```

---

### Post by MarshyTheKid on 2009-02-09
> **geirha said:**
> Not entirely true. Anacron runs the script with whichever shell is in the sh-bang (#!/bin/bash), and bash understands the "~" and replaces it. However, since anacron is run as root, the bash it spawns will also run as root, and ~ will be expanded to /root/ instead of your user's homedir, as it would if you ran it with sudo in a regular terminal.

Also, install the [mailx](apt:mailx) package. If you do that, cron will send you mail when a cronjob fails. You read such mail with the mail command:
```
mail
# or
sudo mail

```It never created anything in the root folder.

---

### Post by geirha on 2009-02-09
> **MarshyTheKid said:**
> It never created anything in the root folder.
Would've if there was a Backup folder in /root/. I'm guessing there isn't one, so that would've given an error like:
```
$ echo something >/path/that/doesnt/exist
bash: /path/that/doesnt/exist: No such file or directory

```

---


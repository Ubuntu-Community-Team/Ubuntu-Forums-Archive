---
title: "Apache, Postgresql, PHP problems"
date: 2008-10-29
forum: Desktop Environments
---

### Post by Vorlin on 2008-10-29
Greetings all,

  I'm running 8.10RC and I'm having a horrible time trying to get apache 2, php 5, and postgresql all working together.

Apache installs and runs just fine but I need php integration for it and for the life of me, I can't get it to work.

PHP through apt-get works just fine but as stated, I need it to be integrated with apache.

Postgresql also installs just fine and works just fine but I can't connect to it because it's not thinking it's running on port 5432 when it is.

Am I missing something stupidly easy or is there a better way to do what I'm trying to do and I just don't know it? Any help would be appreciated.

---

### Post by freelinuxhelp on 2008-10-29
Try this:
sudo aptitude install libapache2-mod-php5

---

### Post by Vorlin on 2008-11-06
Thanks to all the help as that worked perfectly. I did the apt-get purge on the three prior to that and then reinstalled in the manner of apache2, php5, then postgres and it all worked.

---

### Post by freelinuxhelp on 2008-11-06
> **Vorlin said:**
> Thanks to all the help as that worked perfectly. I did the apt-get purge on the three prior to that and then reinstalled in the manner of apache2, php5, then postgres and it all worked.

Now I have another issue, only this time it's with postgresql and php. Any php code I put in for html/php files works just fine but pg_connect won't work because I'm guessing php doesn't have it integrated. How does one change that if it's installed through apt-get?

If I were you, I would mark this thread as Solved (You can di that under Thread Tools), and create a new thread for that issue.

---

### Post by freelinuxhelp on 2008-11-06
Double Post

---

### Post by Vorlin on 2008-11-06
Moving to new topic.

---


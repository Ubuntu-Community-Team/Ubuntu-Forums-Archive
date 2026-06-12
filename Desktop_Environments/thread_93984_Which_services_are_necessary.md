---
title: "Which services are necessary"
date: 2005-11-23
forum: Desktop Environments
---

### Post by goneskiing on 2005-11-23
I am wondering if I can turn off the following services without disrupting anything on my system.

anacron ? (I do not run any specific cron jobs)
atd ?
cron ?
klogd ?
sysklogd?
Kdm ? (I log in with gdm but do run some kde stuff)
fetchmail ? (I use thunderbird)
apache2 ? (I guess I need this for web development stuff but does running this leave me exposed while on the web ?  If so is there a good way to turn on, turn off)

thanks.

---

### Post by Burning Bronx on 2005-11-23
[QUOTE=goneskiing]I am wondering if I can turn off the following services without disrupting anything on my system.

anacron ? (I do not run any specific cron jobs)
atd ?
cron ?
klogd ?
sysklogd?
Kdm ? (I log in with gdm but do run some kde stuff)
fetchmail ? (I use thunderbird)
apache2 ? (I guess I need this for web development stuff but does running this leave me exposed while on the web ?  If so is there a good way to turn on, turn off)

thanks.[/QUOTE]

You can check this How To: [http://www.ubuntuforums.org/showthread.php?t=89491&highlight=howto+speed](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=howto+speed)

It's pretty good (and even better if you know just a bit of what you are doing). As for apache2 if you only use it on ur machine for development u can just make it listen to localhost only. If you tell me what exactly you are doing on it I may give you some other tips.

Cheers.

---

### Post by goneskiing on 2005-11-23
setting it up for localhost only would be fine - I'm just using it for php and postgresql development.

---


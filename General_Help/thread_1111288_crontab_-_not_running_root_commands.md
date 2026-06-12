---
title: "crontab - not running root commands"
date: 2009-03-30
forum: General Help
---

### Post by action_owl on 2009-03-30
**I have created a crontab file using**
[I]
crontab -u myusername -e[/I]

**and I created a test entry:**
[I]
30 14 * * * export DISPLAY=:0 && mousepad[/I]
[B]
this worked so I tried[/B]
[I]
45 14 * * * root wlanconfig ath0 destroy[/I]
[B]
and it did not run...[/B]

avoiding the myusername and using *crontab -e* will not run any command at all.

any suggestions? 
thnx

---

### Post by dcstar on 2009-03-31
> **action_owl said:**
> **I have created a crontab file using**
[I]
crontab -u myusername -e[/I]

**and I created a test entry:**
[I]
30 14 * * * export DISPLAY=:0 && mousepad[/I]
[B]
this worked so I tried[/B]
[I]
45 14 * * * root wlanconfig ath0 destroy[/I]
[B]
and it did not run...[/B]

avoiding the myusername and using *crontab -e* will not run any command at all.

any suggestions? 
thnx

I do not have a command called "root" on my system, what does yours do?

---

### Post by kpkeerthi on 2009-03-31
Put that command in root's crontab

```
sudo crontab -e
```

---

### Post by hyper_ch on 2009-03-31
or make a cron.txt file, add you jobs there and run

```

sudo crontab cron.txt

```

and check it by
```

sudo crontab -l -u root

```

---

### Post by action_owl on 2009-04-17
Sorry for the long response but I had my Laptop stolen and now have Xubuntu on a new one.

My fix for the problem was to create some scripts with the commands I needed to run as root 

example:

SCRIPT:
```

#!/bin/bash
sudo wlanconfig ath0 destroy

```

then I added that script to the sudoers file:
```
sudo visudo

# crontab root scripts
action-owl ALL=(ALL) NOPASSWD:/home/myusername/autoscripts/wdown.sh

```

and then in crontab I put used:
```

00 06 * * * sudo /home/myusername/autoscripts/wdown.sh

```

They've been working great

---


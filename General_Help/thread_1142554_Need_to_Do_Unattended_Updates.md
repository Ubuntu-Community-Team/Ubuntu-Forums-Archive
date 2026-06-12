---
title: "Need to Do Unattended Updates"
date: 2009-04-29
forum: General Help
---

### Post by LaneLester on 2009-04-29
I'm a science teacher with a classroom LAN of 8 Ubuntu clients that need updating (200+ files). These computers are in constant use during the day, so they need to be updated after school. I cannot be present to respond to prompts about keeping or replacing config files and such. Is there a command I can use that will accept the default for all prompts?

Lane

---

### Post by kpkeerthi on 2009-04-29
```
sudo apt-get update && sudo apt-get -y upgrade
```
Perhaps stick that command in sudo's [crontab]("https://help.ubuntu.com/community/CronHowto")

*Its risky to run unattended updates. You have been warned :)

---

### Post by LaneLester on 2009-04-29
Thanks for the solution and the warning. I wish I could do it attended.

These ancient boxes are so slow at everything that I can only update a few at a time.

Lane

---


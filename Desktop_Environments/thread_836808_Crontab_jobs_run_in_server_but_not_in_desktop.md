---
title: "Crontab jobs run in server but not in desktop"
date: 2008-06-21
forum: Desktop Environments
---

### Post by doogy2004 on 2008-06-21
I'm trying to update my computers with a cron job, I understand the risks of automating this process and I'm ok with that.

On my server, running Ubuntu 8.04 LTS Server, I run ```
sudo crontab -e
``` I have the following job which runs fine ```
01 01 * * * date > /home/user/upgrade.log && apt-get update && apt-get upgrade -y >> /home/user/upgrade.log
```

It works great, it runs and outputs to the log so that I can check if there where any problems.

When I do the exact same thing on my desktop, running Mythbuntu 8.04, the job never runs.

They are both fresh installs and I'm at a loss as to what is going wrong.  Thanks in advance.

---


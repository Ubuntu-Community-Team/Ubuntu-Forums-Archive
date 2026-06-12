---
title: "Crontabs"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-06-10
ok so I wanna create a cron job to execute this command every night at midnight

sudo apt-get update && sudo apt-get -fmuy --download-only dist-upgrade

however after reviewing the crontabs documentation I don't see how I can run this as root. I know the -u [username] switch allows me to modify another users crontab but there is no real root account in Ubuntu (the whole sudo thing). 

So how can I run this command in a cron job each night with admin permissions..

Thanks
T3

---

### Post by ns2048 on 2006-06-10
Have you tried 'sudo crontab -e'? Also, take a look at [https://wiki.ubuntu.com/CronHowto](https://wiki.ubuntu.com/CronHowto)

--ns2048

---

### Post by roax on 2006-06-10
Install gnome-schedule. It is in synaptic. I don't know why this isn't a default program.

---


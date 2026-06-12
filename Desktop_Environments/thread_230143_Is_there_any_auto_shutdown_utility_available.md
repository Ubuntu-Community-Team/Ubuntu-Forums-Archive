---
title: "Is there any auto shutdown utility available???"
date: 2006-08-05
forum: Desktop Environments
---

### Post by true_friend on 2006-08-05
I am ubuntu 6.06 user. seeking for some auto shutdown or shutdown timer like utility. some times i want to run system to make some downloads in my absence and for this i need auto shutdown utility to save power.
i tried in root mode shutdown +1 command which i found in some linux forum but in ubuntu it took me to mantainacne mode after 1 minute.
thnx for reading the message.
Regards
True_Friend

---

### Post by ardchoille on 2006-08-05
With crontab, just about anything can be automated. Have a look at my crontab tutorial:

[https://wiki.ubuntu.com/Crontab](https://wiki.ubuntu.com/Crontab)

---

### Post by theo444 on 2006-08-05
I use KShutdown.  Just search the repositories to find it (I think you might have to have the universe repositories enabled though).

---

### Post by louis_nichols on 2006-08-05
well... there are several ways. The +1 thing dows work, except you have to specify exactly what shutdown should do. It can change the runlevel, or shutdown, or reboot etc. So, to shutdown the pc after 1 minute, you use:
```
sudo shutdown -h +1
```

however, I use another method, which I recommend, since you never really know how long a certain task might take. Say for example I want it to upgrade and then shutdown, while I go to sleep. Then, I use:
```
sudo apt-get update && sudo apt-get -y upgrade && shutdown -h now
```
this executes each of the commands after the previous one exited successfully, so it will always be a perfect timing.

EDIT: typo

---


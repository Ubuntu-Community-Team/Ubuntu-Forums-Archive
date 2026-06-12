---
title: "Random Restart"
date: 2006-09-25
forum: Desktop Environments
---

### Post by thegame34 on 2006-09-25
I am fairly new to Ubuntu. So far I love everything I see but I am having an issue. My system will randomly restart on me. I never see this actually happen. It seems to happen if I leave the machine on over night. My girlfriend told me the other day she had it restart on her in the middle of surfing. My question is, is there any logs or anything I can check to see if there are errors on why I am getting a random restart? Any help would be greatly appreciated. Thanks.:confused:

---

### Post by john.nicholls on 2006-09-28
The file to look at is /var/log/syslog. 

cat /var/log/syslog will show you the whole file or
tail /var/log/syslog will show you the last dozen entries.

John

---

### Post by aidanr on 2006-09-28
i've been having similar problems over the last month, ever since i got hooked back up to the net, my pc randomly went blank and i'd have to pull the power cable to restart it, lately it's been randomly restarting

i figured it might be my onboard nic so i replaced it with a pci card, that helped for a day or two and then it started again, i also get a message at boot along the lines of "cannot alocate resource to device region 0000:00:00.0" so i'm thinking maybe it's something on my motherboard

also there is another thread which had similar symptoms that suggested turning off cron, anacron and atd (system - administration - services) so i did that just now to see if that helps

also btw the same thing also has happened running kororaa and gparted live cd and even in my bios, which makes me think that it is a hardware problem

---

### Post by aidanr on 2006-09-29
well, turning off those services didn't make a difference, it just restarted again:(

/var/log/syslog
Sep 29 06:18:25 localhost syslogd 1.4.1#17ubuntu7: restart.

---

### Post by thegame34 on 2006-09-29
Thanks for the advice guys. I am going to check out that log tonight when I get home from work.

---

### Post by aidanr on 2006-10-02
turned out my problem was my psu, replaced it and haven't had any problems since:)

---

### Post by jgeewax on 2006-10-27
I am having this exact same problem. I don't have the bankroll to go out and buy a new powersupply unless I'm 100% sure that this is the problem.

Can any of the gurus comment on this?

If the power supply fails, how is it that the system log daemon can issue a restart command before the power cuts out?

---


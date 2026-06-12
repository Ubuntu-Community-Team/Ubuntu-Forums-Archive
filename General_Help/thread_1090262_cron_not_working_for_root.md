---
title: "cron not working for root"
date: 2009-03-08
forum: General Help
---

### Post by jsvidyad on 2009-03-08
Hi!!

I am running hardy heron(8.04.1)

    I made entries in the crontab for root and it does not do anything. It is just being ignored.My root crontab is given below:

 # m h  dom mon dow   command
15 2 * * * /usr/bin/apt-get -y update && /usr/bin/apt-get -y dist-upgrade
40 7 * * * /usr/bin/poff dsl-provider
45 7 * * * /sbin/shutdown -h now


Can someone please tell me what the problem is??

Thank you in advance.

---

### Post by jld186 on 2009-03-08
Hi, I'm having the same issue with my box. 

# m h  dom mon dow   command
@reboot /usr/sbin/inadyn
0 21 8 3 * echo "" > sudo shutdown -r 5

(came off some website)

I will try your code and see if I can get it to work.

---

### Post by jld186 on 2009-03-08
I threw your code in and edited for my box:

# m h  dom mon dow   command
13 22 * * * /usr/bin/apt-get -y update && /usr/bin/apt-get -y upgrade && /sbin/shutdown -h 5


I get the message that system is going down in 5 minutes, but I can't tell if its doing the other first.  Gonna try to force a log.

That 'echo' junk on my post is wrong then.  Also, did you sudo edit your crontab?  I use > sudo crontab -e

---

### Post by jsvidyad on 2009-03-09
I edited the crontab using contab -e as root.

---


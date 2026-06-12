---
title: "Why does this crontab entry not work?"
date: 2009-04-30
forum: General Help
---

### Post by raz230 on 2009-04-30
I'm kinda new with CRON, but I am logged in as root and I did:

created my crontab with this
crontab -e

placed this command in it
1 * * * * date > /root/date.txt

and checked it with
crontab -l

I restarted cron with 
/etc/init.d/cron restart

in the syslog I see this

Error: bad username; while reading /etc/crontab

I've checked that root owns the crontab and I am writing to root's folder.

If I place the above command in /etc/crontab I get the same error and the other entries in that file do not run below the entry that I add.

I don't understand... 

Rob

---

### Post by dcstar on 2009-05-01
> **raz230 said:**
> I'm kinda new with CRON, but I am logged in as root and I did:

created my crontab with this
crontab -e

placed this command in it
1 * * * * date > /root/date.txt

and checked it with
crontab -l

I restarted cron with 
/etc/init.d/cron restart

in the syslog I see this

Error: bad username; while reading /etc/crontab

I've checked that root owns the crontab and I am writing to root's folder.

If I place the above command in /etc/crontab I get the same error and the other entries in that file do not run below the entry that I add.

I don't understand... 

Rob

a) Do not muck around with /etc/crontab, it is a system file and not meant for users to play with.

b) Do not put commands in cron jobs without full pathnames.

c) Your command will only run on the first minute of each hour.

d) Use the **gnome-schedule** package if you want to experiment with scheduling jobs.

---

### Post by eentonig on 2009-05-01
> **dcstar said:**
> ...
b) Do not put commands in cron jobs without full pathnames.
...


Most likely the issue at hand

---

### Post by dcstar on 2009-05-01
> **eentonig said:**
> Most likely the issue at hand

So you reckon this person is going to sit around at the PC waiting for the first minute of the hour to tick over to see if this test job runs?

---


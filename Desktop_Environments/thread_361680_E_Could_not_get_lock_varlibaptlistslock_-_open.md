---
title: "E: Could not get lock /var/lib/apt/lists/lock - open"
date: 2007-02-14
forum: Desktop Environments
---

### Post by larrybrazos on 2007-02-14
When I try . . .

sudo apt-get update

I get the following error . . .

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list director

This has been happening from me time to time.  I have to complete reboot to fix the problem.  It often happens after I try a sudo apt-get update and could not connect to one of the sources in /etc/apt/sources.list.  When I can not connect I use ctrl-z to stop the update.  I took the link out of sources.list that was giving me problems.

How do I fix this issue?

---

### Post by meng on 2007-02-14
ctrl-z does not stop/kill a process, it just suspends it. Try ctrl-c if you want to stop a process properly.

---

### Post by larrybrazos on 2007-02-14
good to know, thanks.  how can i kill the process now, i am in system monitor looking for what to stop, but i don't seeing anything like "apt-get".

---

### Post by meng on 2007-02-14
Are you looking at all processes, or just ones for your user? I can't be sure, but you could try dropping to command line and:
ps | grep apt
ps | grep sudo
and see what comes up

---

### Post by larrybrazos on 2007-03-09
if anyone else has this problem, i figured it out and have a few tips.

first, as one poster said, use ctrl-c and not ctrl-z to kill processes.

also, this was happening to me because i had a source in sources.list that could not be reached and took a while to timeout, so i would ctrl-c it and lock apt-get.

if you have a source that is giving you trouble . . .

backup sources.list . . .

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup

edited cources.list to remove bad link . . .

sudo gedit /etc/apt/sources.list

delete the dead link.

---

### Post by dabl on 2007-03-10
Which source was dead?  I'm having the exact same problem, but it's not obvious which one is hanging.

Thanks.

---

### Post by larrybrazos on 2007-03-15
hey dabl,

i can't remember what source was hanging, just some random thing i added.

try this . . .

sudo apt-get update

then look at which source could not connect and remove it from the list

---

### Post by maheshjagadeesan on 2007-04-02
When you did a 'ps ax | grep apt', did you notice any scheduled (cron-ed) processes running in the background? I did, and it made me remember that I'd added an "apt-get update" as a daily chore! :-D

---

### Post by ubuntel on 2008-03-04
sudo apt-get clean fixed it for me :)

---


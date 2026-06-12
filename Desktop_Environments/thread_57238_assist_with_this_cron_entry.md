---
title: "assist with this cron entry?"
date: 2005-08-15
forum: Desktop Environments
---

### Post by spudley on 2005-08-15
I've been fiddling around here, trying to get a cron entry to work and am having troubles.. read the wiki, man pages, etc and have things sort of working, but just missing one small detail.

Basically, I like my gdesklets, but one of them must have a memory leak - I kill gdesklets everyday & restart it and memory is recovered.

So, I had this idea, automate the process in cron.

What I need to do is this:
1) kill gdesklets:
```
kill $(pgrep -f gdesklets)
```
2) restart gdesklets:
```
gdesklets
```

So, using that, I loaded /etc/crontab and added:

```
* 3 * * * myusername kill $(pgrep -f gdesklets)
1 3 * * * myusername gdesklets
```
This works great and as expected - HOWEVER, what is going to happen when I have someone other than "myusername" logged in?

In planning for that, I tried my cron entry this way:
```
* 3 * * * $(whoami) kill $(pgrep -f gdesklets)
1 3 * * * $(whoami) gdesklets
```
but that does nothing

**Hmm, as I write this, cron isn't restarting gdesklets for some reason!** 

lets try this:
```
* 3 * * * myusername gdesklets restart
```

That doesn't work either.
(I understand the M H etc format of the crontab entries... My actual entries look like 38 * * * * -- I'm setting minutes to do the testing instead of waiting till 3 am, so that isn't the problem).

Anyway, I think you can see where I'm at -- 

1) how can I pass the current user (whoami) to crontab so this works for all users logged in?
2) why doesn't crontab start gdesklets now (I'm pretty sure it was a few minutes ago... I'll reboot & see if that fixes it).
 --- just rebooted, and same problem - gdesklets isn't reloading with a separate cron entry, nor is gdesklets - restart working as a cron entry.  :???: 



Thanks for any assistance!

---

### Post by astoltz on 2005-08-15
Why not just use root for the user?

---

### Post by spudley on 2005-08-15
Since gdesklets is loaded as the user 'myusername', yes root will kill it in the cron entry, but if I was to load gdesklets (if I get that to work) as user 'root' will it show up while a user other than 'root' is logged in?

---

### Post by TrD on 2006-05-17
Spudley, did you get this to work?
Im having the same problem with gdesklets and crontab.

---


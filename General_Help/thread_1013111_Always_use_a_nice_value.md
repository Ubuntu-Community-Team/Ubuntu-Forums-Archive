---
title: "Always use a nice value"
date: 2008-12-16
forum: General Help
---

### Post by Nonno Bassotto on 2008-12-16
I know I can assign different priorities to programs modifying their nice value. Is there a way to tell the system "always use this nice value for program x?" In particular I would like to be able to use synaptic, dpkg, apt-get or whatever with a low priority. I don't care if updates or new installs take 5 or 10 minutes, as long as they don't slow down the pc, so I'm able to do other things in the meantime.

---

### Post by kerry_s on 2008-12-16
hmm, i'm using 450mhz 256mb ram and can run those programs with no slow down.

look at reniced, it's in the repo.

---

### Post by Nonno Bassotto on 2008-12-16
I have a laptop with 512MB and a CeleronM, I think with 1.5 Ghz, and the slowdown is noticeable. I will have a look at reniced. :)

---

### Post by Nonno Bassotto on 2008-12-16
Uhm... it seems that it has to be executed every time. I don't think it will work because synaptic will call different instances of apt-get and dpgk I think. I was looking for something which constantly monitors processes.

For instance trackerd always starts with a nice of 19. How is this done?

---

### Post by doobiest on 2008-12-16
Googling suggests no, but one thing you could do is have a cron run a quick script to do this, but it's on a per application basis.

I haven't look to far into it but here's a simple example it's dirty but would work

I'm going to renice bash every 1 minute, if this was put in crontab

for list in `pidof bash`;
do 
renice 1 ${list}; 
done

I would never want to use this script, but just wanted to show a simple example of how to take an array of PIDs and renice them.

Perhaps someone can build on it

---

### Post by doobiest on 2008-12-16
additionally you could make an alias in .bashrc

alias apt-get='apt-get $1 $2; renice 1 `pidof apt-get`'

This doesnt work, i'll edit once done, but im hoping someone can filli in the blanks for me

alias apt-get='sleep 2 && renice 1 `pidof apt-get`& apt-get $1 $2'

This is dirty but would work, this would go in root's .bashrc

Additionally I was noticing you can renice based on user, so I guess you could have all of the root user's processes run low priority and have the main user have priority but I'm not sure what ill effects would come.

---

### Post by Coreigh on 2008-12-16
I script the updates to happen automatically and during off hours.

I am sorry I can not offer a link to a how-to but I put it in my cron weekly to run the update script below.

> #! /bin/bash
# update software packages
apt-get update
apt-get upgrade -y
apt-get autoclean

# update locate DB
updatedb


It does everything automatically so you are vulnerable to a bad update if one happens.

---

### Post by Nonno Bassotto on 2008-12-17
> **doobiest said:**
> Googling suggests no, but one thing you could do is have a cron run a quick script to do this, but it's on a per application basis.

I haven't look to far into it but here's a simple example it's dirty but would work

I'm going to renice bash every 1 minute, if this was put in crontab

for list in `pidof bash`;
do 
renice 1 ${list}; 
done

I would never want to use this script, but just wanted to show a simple example of how to take an array of PIDs and renice them.

Perhaps someone can build on it

Even if you do this once a minute... well you have a one minute lag, which is not so good. In the same time I can open system monitor and renice every process manually. It should be a daemon working with d-bus or something, or even better synaptic should be automatically called with a high nice.

---

### Post by Nonno Bassotto on 2008-12-17
> **doobiest said:**
> additionally you could make an alias in .bashrc

alias apt-get='apt-get $1 $2; renice 1 `pidof apt-get`'

This doesnt work, i'll edit once done, but im hoping someone can filli in the blanks for me

alias apt-get='sleep 2 && renice 1 `pidof apt-get`& apt-get $1 $2'

This is dirty but would work, this would go in root's .bashrc

Additionally I was noticing you can renice based on user, so I guess you could have all of the root user's processes run low priority and have the main user have priority but I'm not sure what ill effects would come.

This would be what I want, but will it work for bash only? What if I call synaptic through a menu, or if synaptic calls an instance of apt-get?

---

### Post by doobiest on 2008-12-17
Ya I really wouldnt use that.. 

I do like this better but it still sucks

alias apt-get='sleep 2 && renice 1 `pidof apt-get`& apt-get $1 $2'

---


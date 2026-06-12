---
title: "apt-get update failed...."
date: 2006-09-12
forum: Desktop Environments
---

### Post by SirShaggy on 2006-09-12
I just tried to do an update, this is what I got.

shaggy@shaggy-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)

Any ideas here? I am really not sure what I did this time....

SirShaggy

---

### Post by unisol on 2006-09-12
do you have another package manager open if you do close it and try again

---

### Post by ayoli on 2006-09-12
> **SirShaggy said:**
> 
shaggy@shaggy-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
SirShaggy

this leads me to think you have a network problem (ie: bad DNS) or a bad /etc/apt/sources.list file (ie: bad repos adresses).

---

### Post by SirShaggy on 2006-09-12
Not sure what was up. I waited 10 minutes, tried it again and it worked.
I had been online all day, working and surfing. Never had another issue like this. I have 1.5Meg DSL, always on, always connected and never had an issue.
I was able to go onto my other system and do an update when this one wouldn't. Maybe it was a fluke. Anyway, thanks for your replies, I will keep this going incase........

SirShaggy

---


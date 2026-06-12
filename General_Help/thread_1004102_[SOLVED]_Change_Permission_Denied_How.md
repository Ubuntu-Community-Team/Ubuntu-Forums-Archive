---
title: "[SOLVED] Change Permission Denied How ?"
date: 2008-12-06
forum: General Help
---

### Post by Rodney9 on 2008-12-06
> ~$ rtcwake -u -s 1800 -m on 
/dev/rtc0: Permission denied

If I use the above it says Permission Denied.
How do I use it then without sudo so I don't have type a password ? I wont be at the machine when it runs in "Alarm Clock"

Rodney

---

### Post by vishzilla on 2008-12-06
try this command to change the ownership ```
sudo chown user.group /dev/rtc0
```
group will be your username

---

### Post by Rodney9 on 2008-12-06
> **vishzilla said:**
> try this command to change the ownership ```
sudo chown user.group /dev/rtc0
```
group will be your username

Thanks for trying but I get the following -

$ sudo chown user.rodney /dev/rtc0
chown: invalid user: `user.rodney'

rodney is my user name, any clues ?

Rodney

---

### Post by f37u5g0d on 2008-12-06
What if you run gksudo nautilus and navigate to that folder and change the permissions of rtc0 so that "rodney" has full read, write, and execute?

---

### Post by Slim Odds on 2008-12-06
> **Rodney9 said:**
> Thanks for trying but I get the following -

$ sudo chown user.rodney /dev/rtc0
chown: invalid user: `user.rodney'

rodney is my user name, any clues ?

Rodney

```
sudo chown rodney.{group} /etc/rtc0
```replace {group} with the group that you want

---

### Post by Rodney9 on 2008-12-06
> **Slim Odds said:**
> ```
sudo chown rodney.{group} /etc/rtc0
```replace {group} with the group that you want

Thanks, but what group would I use ?

I used man group and help group, they talk about managing groups but I can't find which groups are what.

Rodney

---

### Post by Slim Odds on 2008-12-06
In your case, you can probably just skip the group

---

### Post by Rodney9 on 2008-12-06
Thank You Slim Odds > $ sudo chown rodney /etc/rtc0 did the trick

Thanks Again,
Rodney

---


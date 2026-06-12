---
title: "Programmable login manager"
date: 2007-01-22
forum: Desktop Environments
---

### Post by lduperval on 2007-01-22
Hi,

Is there a way to block certain logins at certain times? Basically, I have some young children who always want to mess around with the computer. I want to prevent them from being able to log into the system except at certain times (weekends, usually).

Some kind of override would be useful also. that way, if they need to use it for schoolwork during the week, I can let them in.

Does something like this exist. I use GNOME mainly.

Thanks,

L

---

### Post by daemonoid on 2007-01-24
There may be an easier way, but i'd try a login script.

create a new script file and add it to the bashrc (or /etc/profile if you prefer)

Then use the date command to check against times and dates that you do or don't allow. otherwise call the shutdown command to turn off the pc.

If you require help writing the script then post back and I (when i have a little more time) or someone else will give you a hand.

---

### Post by nocturn on 2007-01-24
Take a look at /etc/security/time.conf

---


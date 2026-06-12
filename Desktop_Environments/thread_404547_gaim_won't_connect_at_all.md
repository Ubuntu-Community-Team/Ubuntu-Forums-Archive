---
title: "gaim won't connect at all"
date: 2007-04-08
forum: Desktop Environments
---

### Post by isaacjoe on 2007-04-08
Gaim has always worked wonderfully for me, MSN messenger sporadically but I mostly use AIM so it was OK. But about a week ago everything started not working at random intervals--aim and msn, and neither one has worked for me at all since about monday or tuesday. I boot into windows and aim works great, aim express works, but not gaim in ubuntu. I took a screenshot of what it looks like:

[img]http://img63.imageshack.us/img63/9199/gaimscreenaf9.jpg[/img]

Any suggestions, I am at a total loss. This is the new beta 6, I upgraded in the hope that the issue would be resolved with the new version. I was using beta 3.1 before and the problem was identical

---

### Post by isaacjoe on 2007-04-08
Bump, still completely stumped. I left my laptop on all day and came back and AIM had mysteriously signed on. I'm thinking it may be a problem with IPV6? I know I had to set firefox to disable IPV6/TRUE when I installed Ubuntu.

I will happily spit out error logs, etc if someone would point me in the right direction. Forum searching hasn't helped me much

---

### Post by isaacjoe on 2007-04-12
Bump

---

### Post by kerry_s on 2007-04-12
You can block it with:

sudo gedit /etc/modprobe.d/bad_list

put

alias net-pf-10 off

---

### Post by isaacjoe on 2007-04-13
Still nothing, I tried adding that entry, saving, restarting, still nothing. So I commented it, restarted, still says that the network is unreachable. Even though I am typing this message from the same installation of ubuntu, firefox works great. Maybe this will be resolved in ubuntu 7 in six days?

---

### Post by TMBridge on 2007-04-16
I am having the same problem.  Kopete works fine for me.  I've reinstalled multiple times and tried everything here.  Any other ideas?

---

### Post by dominicd on 2007-04-19
> **isaacjoe said:**
> Bump, still completely stumped. I left my laptop on all day and came back and AIM had mysteriously signed on. I'm thinking it may be a problem with IPV6? I know I had to set firefox to disable IPV6/TRUE when I installed Ubuntu.

I will happily spit out error logs, etc if someone would point me in the right direction. Forum searching hasn't helped me much

If it's a problem with IPV6 you can disable IPV6 completely for afaik as follows

run in terminal:
```
gksudo gedit /etc/modprobe.d/blacklist
```


and add the following line:
```
blacklist ipv6
```

---


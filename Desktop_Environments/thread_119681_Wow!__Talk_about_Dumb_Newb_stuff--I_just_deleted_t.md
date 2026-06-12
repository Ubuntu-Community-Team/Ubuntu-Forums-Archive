---
title: "Wow!  Talk about Dumb Newb stuff--I just deleted the root user on my box"
date: 2006-01-20
forum: Desktop Environments
---

### Post by ubuntunewb75 on 2006-01-20
Ok seems dumb, but I deluser root on my box after trying to get the CUPS web interface working--I tried to boot in single mode but it can't find the root password (obviously).  What are my options on recovery?  the system boots fine, I just can't sudo or do anything with administrator priviledges. Please be gentle as I have aloready beaten myself about the head with a large pan (figuratively).

---

### Post by slashem on 2006-01-20
Edit /etc/passwd and add
root:x:0:0:root:/root:/bin/bash
at the top (may have to use a livecd)
Reboot into single user and type passwd

I've never had to do this so I'm just guessing here, this may or may not work... :)

---


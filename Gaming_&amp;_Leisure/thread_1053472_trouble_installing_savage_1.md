---
title: "trouble installing savage 1"
date: 2009-01-28
forum: Gaming &amp; Leisure
---

### Post by c/Kr3t on 2009-01-28
i'm following this guide [http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux](http://czarism.com/how-to-install-savage-on-ubuntu-debian-linux) and i get these errors

the downloading of the file works, it's just installing that that fails

```
on0bi@on0bi-desktop:~$ wget http://downloads.s2games.com/online_orders/savage_linux.sh.gz
--2009-01-28 14:51:39--  http://downloads.s2games.com/online_orders/savage_linux.sh.gz
Resolving downloads.s2games.com... 216.127.42.161
Connecting to downloads.s2games.com|216.127.42.161|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 330693936 (315M) [application/x-sh]
Saving to: `savage_linux.sh.gz'

100%[======================================>] 330,693,936 38.2K/s   in 1h 57m  

2009-01-28 16:48:53 (45.9 KB/s) - `savage_linux.sh.gz' saved [330693936/330693936]

on0bi@on0bi-desktop:~$ gzip -d savage_linux.sh.gz
on0bi@on0bi-desktop:~$ sh savage_linux.sh
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 373431374 1439400631

```

---

### Post by Naiki Muliaina on 2009-01-29
Ive seen that problem a couple of times on the forum. The only advice folk get is to follow this guide: [http://gaming.gwos.org/doku.php/guides:64bit:savage_1](http://gaming.gwos.org/doku.php/guides:64bit:savage_1)

Wether it works or not i dont know because nobody seems to reply  ^^

---

### Post by c/Kr3t on 2009-01-29
hey thanks, it works now

---

### Post by Naiki Muliaina on 2009-01-29
*Puts on heroic narrator voice and booms*  

"And once again UGA's guides saved the day!" ^^

Very good site, always a first port of call when you have trouble installing something ^^

---


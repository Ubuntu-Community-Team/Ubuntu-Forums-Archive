---
title: "Multiple Partion Install"
date: 2009-01-20
forum: General Help
---

### Post by beattyml1 on 2009-01-20
I am looking do do a fresh reinstall of ubuntu and I want to try a multi-partition install with at least having separate swap, /, and /home partitions, I would like to know first off what other separate partitions if any would you suggest creating, as well as how large I should make each partition, I would like to try to get at least 150 GB for my /home partition and more if you think it would be advisable

I have a 250 GB HD but after My dual boot with Ubuntu Studio I will only have 194 GB 

I have 4 GB of RAM

---

### Post by CAPLinux on 2009-01-20
Beattyml1,

I only run three partitions /, /home and swap.  I have a 3gb swap partition and it is completely overkill.  I have 2GB of ram and it never users that partition at all.  Because of that, I would suggest only 1GB swap partition.  

For the / partition 10GB would be enough, you could do as much as 20 GB but that may be a bit much.  Then leave the rest for your /home partition.

---

### Post by Achetar on 2009-01-20
Mount a tmpfs (RAMDisk) on /tmp if you have more than 1GB of RAM. It can greatly improve system performance imxp. ( /tmp is cleared on every shutdown, so it's not like you are actually losing anything)

```

/dev/ram0 /tmp tmpfs user 0 0

```CAPLinux is right: 
20GB /
2GB swap
172GB /home
( I have a separate /multimedia partition that I keep Music, Movies, etc. on)

You could also keep /etc on a separate partition, in case your / gets corrupted, you keep all your configuration files (or at least most of them). If you are a web developer having your webroot on a separate partition helps a ton.

Example:
2GB /etc
5GB /your/web/root (default is /var/www, i use /srv usually )

---


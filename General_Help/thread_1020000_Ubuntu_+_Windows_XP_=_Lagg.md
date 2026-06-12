---
title: "Ubuntu + Windows XP = Lagg?"
date: 2008-12-23
forum: General Help
---

### Post by retskrad on 2008-12-23
I have windows XP installed with no program installed. If I then install Ubuntu, will the computer get slow?

---

### Post by oilchangeguy on 2008-12-23
> **retskrad said:**
> I have windows XP installed with no program installed. If I then install Ubuntu, will the computer get slow?

shouldn't. how are you planning on installing ubuntu?

---

### Post by yipperzz on 2008-12-23
if you're dual booting, it'll be the same speed.

---

### Post by retskrad on 2008-12-23
I will install it with wubi.

Will it be slower if I install it with wubi, or should I burn the iso to a DVD?

I installed the iso from the website and then burned the iso on a DVD+RW disc. I burned it with max speed.

When I removed everything including windows xp and put in the ubuntu install disc, I get an error that I should clean the disc, or hardware problems or I should Use the slowest speed. 

I don't know should I use wubi or burn it to a dvd disc and install? Will it be any difference?:P

---

### Post by retskrad on 2008-12-23
Bump

---

### Post by jerome1232 on 2008-12-23
Running a wubi install Ubuntu will have slightly slower disk access times than if it were a true install of Ubuntu.

Wubi will in no way affect the speed of your Windows OS.

If you plan on keeping Ubuntu around I would do a real install, however Wubi is nice if you don't feel comfortable with repartitioning your disk.

---

### Post by retskrad on 2008-12-23
I will use Ubuntu almost all the time, maybe somestimes, very few occations I will be using XP. I should do a clean install instead?

---

### Post by retskrad on 2008-12-23
******* piece of **** Internet Explroer... I just downloaded Ubuntu ISO and it was 56 % and IE crashed! WTF!

---

### Post by retskrad on 2008-12-23
bump

---

### Post by oilchangeguy on 2008-12-23
> **retskrad said:**
> bump

so ie crashed. that means you get to try again. how would you expect those here in the forum to be able to answer why ie crashed. it's probably something to do with your isp. and you'll find you'll get better responses if you'll stop bumping your thread. that just makes people ignore you.

---

### Post by jmszr on 2008-12-23
retskrad,
           I would suggest that you read this: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  , As I recall Windows has a habit of crashing at inopportune times (as if there is an opportune time). Wubi works well - make sure to defrag before installing if that's what you decide to do. If you go dual boot burn your .iso at a slow speed (2x-4x). By the way a CD (700MB) will work just fine. But do read psychocats.

---

### Post by TeXtonyx on 2008-12-23
> **retskrad said:**
> ******* piece of **** Internet Explroer... I just downloaded Ubuntu ISO and it was 56 % and IE crashed! WTF!

Use Firefox, it is cross-platform working on Linux and Windows.
And if you want, you can share your Firefox profile.

If you want to keep your XP partition separate, then install
grub to the /boot partition during Step 7, Advanced of the 
Ubuntu live cd install. I think you should create the partition
beforehand with Gparted. Then choose to install Ubuntu to the
largest continuous unallocated space. You will need Bootpart
to boot Ubuntu if you install grub to the /boot partition.
A free download, it creates a 512 byte linux.bin and writes
to boot.ini. Read the directions. Find bootpart using google.

---

### Post by retskrad on 2008-12-23
I know my man, I have never used IE, Ihave always used firefox.

---

### Post by Wisp558 on 2008-12-23
Try downloading using the torrent. Utorrent works great for XP. When I use 'dows I use utorrent. Torrents are 100% legal, and they automatically correct errors, suport download resumption and so on.

It also helps save bandwidth.

---

### Post by retskrad on 2008-12-23
I'll install with wubi. Do you think there'll be reduced performence?

---


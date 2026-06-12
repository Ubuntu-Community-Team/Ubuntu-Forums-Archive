---
title: "making ubuntu think new HDD is part of old HDD...possible?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by delfick on 2006-07-04
hello all

when i installed Ubuntu i put it on my existing hardrive as a new partition of just under 10Gb. Unforunataley i want more now and there isn't enough space to repartition, as i am leaving space on the old hardrive so i can install more cool games on my windows partition as they come out in the future.

So i got myself a 20gb hardrive off a friend.

I was wondering...when i put it in my computer, am i able to make ubuntu think that this new HDD is part of the old HDD. So that as i install new applications from the repositorys, there is enough room in the main folder place where these things are installed 

if that makes sense to anyone (i'm still a newb...:D)

thnx for help, much appreciated...

---

### Post by jethro10 on 2006-07-04
Yes,


does this help [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

J

---

### Post by aysiu on 2006-07-04
Well, a few things here...

1. You can make more space by cleaning out all the installation files for your applications: ```
sudo apt-get clean
``` This empties the /var/cache/apt/archives folder, where you'll see a lot of .deb files that take up space.

2. Instead of moving your /usr folder to a new drive, you may want to move your /home folder instead. I have a ton of programs and three desktop environments installed on my Ubuntu, and my entire installation is 3.3 GB. Most of my used space on a separate partition is my music, pictures, webpages, and other documents.

For that, this guide should help: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by delfick on 2006-07-04
thnx for that peoples :D

looks very helpful....i'll tell u if it works when i get around to putting the harddrive in my computer

...:D

---

### Post by delfick on 2006-11-11
> **aysiu said:**
> For that, this guide should help: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

well, i've finally got around to moving the home partition :D

thnx for the link....i followed it and it seems to work :D

only problem is that the hardrive is no longer considered an extra hardrive and so doesn't appear under /media/hdc1 (which some programs link to) and also doesn't put a shortcut of itself on the desktop (which i really want back :D)

thnx for help :D

---

### Post by sjokki on 2006-11-11
You can mount a partition multiple times at different mount-points.

---

### Post by delfick on 2006-11-11
> **sjokki said:**
> You can mount a partition multiple times at different mount-points.

Well, it seems to have fixed itself on turning the computer back on this morning, so all is good :D


though i'll remember that for the future, thnx :D

---


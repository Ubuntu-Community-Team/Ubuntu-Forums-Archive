---
title: "Harddisk filled randomly?"
date: 2008-12-23
forum: General Help
---

### Post by llarz on 2008-12-23
Pardon my newbness, I've just recently switched to the wonderful world of linux from windows.

I've been pretty good so far. I'm currently dual booting vista and ubuntu, with ubuntu on a 10 gig partition (I plan to increase this soon).

I've filled about 85% of my disk space. Just a few hours ago I left home leaving this PC on, and came back to my hard disk being 100% full - I haven't a clue how this happened; no downloads were taking place or anything.

Looking at the Disk Usage Analyzer I'm seeing /var containing 3 gigs, /usr with 2.9 and /home with 1.7.

Are these values high? Any ideas on what could have filled that remaining ~2 gigs of space within an hour?

---

### Post by Monotoko on 2008-12-23
The rest of your install will take a fair bit...i dont know if it would total 3GB though....try and increase the partition size to 20GB and see what happens

---

### Post by llarz on 2008-12-23
Well, I rebooted into Recovery Mode, did a filesystem check and tried the Clean (forget the extra name of the option), and it's dropped from 100% used to 70%. I'm still not sure exactly what happened to cause it to fill so much, /var is now much smaller, /usr a fair amount smaller.

I do plan on resizing my partitions as I rarely use my vista install on this laptop, mostly Ubuntu for university stuff. I'm a little hesitant on doing that right now until I look up some more about safely resizing my partitions as to not loose everything :P

---

### Post by jerome1232 on 2008-12-23
/var is where logs are kept, also that's where archived packages get kept. Could you have some errant program logging away like a madman?

---

### Post by llarz on 2008-12-24
Well, Mercury Messenger did have an error when I returned... perhaps it was spazzing out? hehe

---


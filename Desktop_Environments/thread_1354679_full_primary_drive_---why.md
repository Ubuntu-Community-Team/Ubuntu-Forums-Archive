---
title: "full primary drive ---why?"
date: 2009-12-14
forum: Desktop Environments
---

### Post by Dan Z on 2009-12-14
Running 8.1
Primary drive is 66GB. Normally it had 28 GB free. Now it is full. SO 28 GB got filled, I know not how. I did not fill it.

If I look at the contents of the drive it does not show what the 28 GB consists of. So the 28 GB is a mystery. 

Any tips on how to find the problem and restore my empty space?

Thanks Dan

---

### Post by i.r.id10t on 2009-12-14
Update files, logs, etc?  First open a terminal and do 

sudo apt-get clean

And check your disk space - you should see some opened up.

---

### Post by Dan Z on 2009-12-14
> **i.r.id10t said:**
> Update files, logs, etc?  First open a terminal and do 

sudo apt-get clean

And check your disk space - you should see some opened up.
thanks, but it did not make a significant difference. I gota believe that the 28G that popped in to fill my drive is some sort of corruption. I ran Bonager boot scan, and says all ok. Dan

---

### Post by TitanusEramius on 2009-12-14
I've try to run baobab in the terminal to get a sense of where the space is used, it should open a little peace of software you can scan the filesystem / with.

Te

---

### Post by Dan Z on 2009-12-15
> **TitanusEramius said:**
> I've try to run baobab in the terminal to get a sense of where the space is used, it should open a little peace of software you can scan the filesystem / with.

Te
Yes I ran that, but the missing GBs do not show up. It is like the extra GBs are not part of the filesystem, or cannot be read. Same results if you look at the drive using command line in terminal.

---


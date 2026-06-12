---
title: "clone systems"
date: 2006-08-17
forum: Desktop Environments
---

### Post by joefie on 2006-08-17
Hello all

i have 7 identical systems, I installed ubuntu on 1 of them. I would like to clone it to the other systems by cd/dvd. How can this be done?

- Joefie

---

### Post by Redache on 2006-08-17
Can you elaborate at all?. If you mean just install it on each system then use the CD, if not then I'm not sure.

---

### Post by joefie on 2006-08-17
I would like to duplicate(clone) my ubuntu installation on other identical systems, through cd/dvd...

---

### Post by ardchoille on 2006-08-17
> **joefie said:**
> Hello all

i have 7 identical systems, I installed ubuntu on 1 of them. I would like to clone it to the other systems by cd/dvd. How can this be done?

- Joefie

I use partimage to do this on 11 machines. Here are the steps I take:

1. Install and update Ubuntu on one machine
2. Install and config all the apps I want to use on that machine
3. Use partimage to make clone image(s) of the partition(s)
4. Burn the image(s) to a DVD (partimage uses compression to keep the image size down)
5. Install Ubuntu to the other machines (NOTE: this is not needed if you don't mind manually setting up grub on the other machines, but I did it to keep from doing that)
6. Use partimage to install the burned image(s) to all other machines
7. Config the hardware settings on the other 10 machines

I ended up with 11 identical machines following this method and it saved a lot of time.

You can find partimage in the repos, but I used the System Rescue CD available from: [http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

You can use a MEPIS livecd as it had partimage on it as well.

---

### Post by kpkeerthi on 2006-08-17
Backup entire partition...
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by joefie on 2006-08-18
i'm searching for a unattended recovery instalation/recovery, so just put cd in en voila system restored

---

### Post by bazzer on 2006-08-18
I'm searching too, but I've so far used the method ardchoille listed. It's not exactly pretty but it does work...

In my limited experience, FAIs just don't seem to work with CD installs.

---


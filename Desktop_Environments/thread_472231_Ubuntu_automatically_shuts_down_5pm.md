---
title: "Ubuntu automatically shuts down 5pm"
date: 2007-06-12
forum: Desktop Environments
---

### Post by NJC on 2007-06-12
I'm usually not home to witness this but it appears that Ubuntu 6.06 is shutting down automatically at 5pm every day. 

My BIOS does not have this feature. The only anomaly is that my system clock and Ubuntu are always 5-6hrs (can't recall which one) apart. Resetting system clock doesn't seem to help and it appears to be a problems between BIOS, Win98 and Ubuntu.

Any suggestions?

---

### Post by tgoose on 2007-06-12
I don't know about the restarting problem, but the clock being wrong sounds like you have set it to use UTC when your computer doesn't. To remedy this, right click on the date/time in the top right, go to preferences and untick Use UTC. If it's already unticked then I don't know what the problem is, I'm afraid.

---

### Post by NJC on 2007-06-12
tgoose;

Thanks. Use UTC was already unselected. 

Just figured out what is was. For whatever reason, Hibernate in Dapper causes my PC to turn off ... and I had it selected to Hibernate after one hour.

---


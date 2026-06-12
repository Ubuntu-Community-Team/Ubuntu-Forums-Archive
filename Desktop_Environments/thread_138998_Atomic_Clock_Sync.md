---
title: "Atomic Clock Sync?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by nmastae on 2006-03-03
Can anyone tell me how to get Ubuntu to sync with the Atomic Clock?

---

### Post by akiro.yamamoto on 2006-03-03
Right click on the clock select Adjust Date & Time.
You will be asked for your Password.
Then on the Time and Date Settings Dialog.
Select Synchronize Now.
Done

---

### Post by nmastae on 2006-03-08
Thank you. Very easy. Very nifty.

---

### Post by Madpilot on 2006-03-08
You can set synchronization to happen automatically, too. (It's supposed to happen during boot, but IME that often fails.)

Open the clock dialogue like akiro.yamamoto said, then tick **Periodically synchronize clock with internet servers**.

Next hit the **Select Servers** button. Rather than picking servers at random and hoping they work, type *pool.ntp.org* in the white box, hit the **Add** button, then scroll right down to the bottom of the server list and make sure the new addition is checked.

*"The pool.ntp.org project is a big virtual cluster of timeservers striving to provide reliable easy to use NTP service for millions of clients without putting a strain on the big popular timeservers."* -- from [http://www.pool.ntp.org/](http://www.pool.ntp.org/)

This seems to work - my own machine has been set up this way for about 6 months and is still right on time.

---

### Post by Howlin' Hobbit on 2006-10-15
Thank you akiro.yamamoto and Madpilot!

I've had Ubuntu on my laptop for a little over a week now and it's getting closer to completely replacing the functionality of my regular PC with Windoze 98. This was another chip away at it.

Once I get it to where it does all of my "normal" stuff I'm planning to put Ubuntu on the regular PC as well.

---

### Post by abutua on 2006-11-09
Hi, I have the same problem. I cannot synchronize my clock. Everytime I try to do it, I always need to install NTP first. I downloaded it already, and tried to compile it. But it never worked. Could you tell me how to install NTP and compile it?
Thanks.

---

### Post by CatKiller on 2006-11-10
I thought all the NTP stuff was installed by default? Anyway, the packages are in Synaptic - there's no real need to compile them from source.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---


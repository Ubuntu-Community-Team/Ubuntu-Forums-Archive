---
title: "multi user eject problem: user A inserts CD &gt;&gt; User B cannot eject."
date: 2006-01-30
forum: Desktop Environments
---

### Post by sander marechal on 2006-01-30
Hello,

I've run into a little snag on my PC. When I enter a CD a little CD icon apperas on my Desktop. Great. I use right click >> eject to eject it. If I leave the CD in, the icon is still there after I reboot, and I can still eject with right mouseclick >> eject. All is well. 

Now, I start up the PC and I log in. Next, my girlfriend comes along and she chooses Applications >> System Tools >> New Login, she logs in as herself an tries to eject the CD. She gets a message that only my account can eject the CD, not hers.

My girlfriend and I have exactly the same rights on the system (all flags enabled in System >> Users and groups). How can I make it so that, when my girlfriend does right click >> eject, that it ejects a CD that I inserted?

Thanks a lot!

---

### Post by dcstar on 2006-01-30
[QUOTE=sander marechal]Hello,

I've run into a little snag on my PC. When I enter a CD a little CD icon apperas on my Desktop. Great. I use right click >> eject to eject it. If I leave the CD in, the icon is still there after I reboot, and I can still eject with right mouseclick >> eject. All is well. 

Now, I start up the PC and I log in. Next, my girlfriend comes along and she chooses Applications >> System Tools >> New Login, she logs in as herself an tries to eject the CD. She gets a message that only my account can eject the CD, not hers.

My girlfriend and I have exactly the same rights on the system (all flags enabled in System >> Users and groups). How can I make it so that, when my girlfriend does right click >> eject, that it ejects a CD that I inserted?

Thanks a lot![/QUOTE]
In /etc/fstab, if the cd-rom mount option says "user", change it to "users".

---

### Post by sander marechal on 2006-02-07
Thanks!

---


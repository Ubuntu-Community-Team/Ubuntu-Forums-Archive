---
title: "System crashed now cannot login"
date: 2009-02-03
forum: General Help
---

### Post by vtrader on 2009-02-03
This is what happened, I added a new user, I then tried to switch to another user and the system crashed. Fair enough, I am using fglrx drivers. But anyway after the reboot, kdm did not start because all I seemed to get was chown invalid user errors in the boot process. 

So I thought the passwd and group files where involved. So I used a liveCD to get into the partition, and I was correct both the passwd and group files were empty. Luckly there were two files called group- and passwd- which seemed to resemble something usuable. So I copied them in group and passwd. REbooted.

This time the boot process made is all the way to with no errors the kdm screen. But I still cannot login(kdm or ttys), it is as if my user accounts still do not exit.
Am I missing something, did I forget to change something?

Thanks.

---

### Post by vtrader on 2009-02-03
the plot thinkens, the file shadow also needed to be recreated. However everytime I reboot it becomes empty. Any ideas?

---


---
title: "Wireless network does not wake up"
date: 2008-12-30
forum: General Help
---

### Post by Elijah2104 on 2008-12-30
I am having trouble with my built in wireless network card.  

The only way I can describe the problem is that after a short period the network connection ceases.  Sometiems this happens after a period of inactivity, but I can be accessing the hard disk of the machine and it drops during use.

If I run the commands:

```
rmmod rtl8187
modprobe rtl8187
ifconfig eth0 up
ifconfig wlan0 up
```

it will sometimes wake up again.  I have read in a few places that there is a script which can execute automatically to do this on wake up.  I've tried the suggested ones (even though I can't remember where there are now) and stil nothing.

To be honest, what I would really prefer is for the wireless not to shutdown at all because I want to be able to access it from anywhere without having to do anything to the PC itself.

If that can't be achieved though, having it wake up properly will be a step in the right direction.

Is anyone able to assist me?

Thanks in advance.

---

### Post by Elijah2104 on 2009-01-07
I've just learnt that this problem is a bit more extreme than I thought.  It actually timed out while I was using it.

The above four commands successfully woke it up again but surely this means it can't have anything to do with the machine going to sleep?

Is anyone able to help with this?

---

### Post by Elijah2104 on 2009-01-07
I've just found the networking category on this forum, so I've now reposted this [here]("http://ubuntuforums.org/showthread.php?p=6511159#post6511159")

Apologies for mis-posting :)

---


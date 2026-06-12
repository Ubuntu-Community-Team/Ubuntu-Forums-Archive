---
title: "Wireless not working after latest update"
date: 2008-11-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eyime on 2008-11-14
Hi everybody,

recently I purchase a DELL XPS M1330 with Ubuntu 8.04 LTS, I was very happy with this product until yesterday, when the system required me a reboot after the kernel update. Well, the problem is that after the reboot the wireless card is not working.

I was trying to undo the changes of the update, but it seems that Ubuntu doesn't have a easy way to do this.

Any suggestion, please ...

---

### Post by iponeverything on 2008-11-14
if you can post the output of:

```
lspci 

```
and

```
lsmod 

```
and 

```
iwconfig

```

and
```
sudo -i
cd /root/.synaptic/log/ ; cat `ls -tr|tail -1`
exit

```

---

### Post by eyime on 2008-11-14
Thanks for your reply,

well, I guess the problem will be the router in my company, because in my home the wireless is working. However yesterday everything was fine.

---

### Post by eyime on 2008-11-16
I found the problem, the routers were changed in my company, but it seems there were so many mac address stored in the applet for wireless connection, so I deleted all wireless network configurations, and configure it again.

---


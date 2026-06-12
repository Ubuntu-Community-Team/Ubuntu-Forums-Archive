---
title: "Messed up eth0 settings"
date: 2009-01-13
forum: General Help
---

### Post by RuleMaker on 2009-01-13
Ok, here is what happened...
I've been messing around with my router settings to forward my port in order to get my apache server working...I messed up my router settings so I wasn't able to access my router or any site anymore. Then I tried to fix that problem with ifconfig, but I made just more trouble to me.
I called my provider and they fixed the problem in my router, but I still cant use my internet connection and I know its a problem in my system settings, since I'm using the same connection now from the live CD and everything works fine.
Is there any way to undo changes or automatically configure eth0?
My english is not the best yet but I hope you understood me, please help :(

---

### Post by albinootje on 2009-01-13
> **RuleMaker said:**
> 
Is there any way to undo changes or automatically configure eth0?


Can you post the output of :
```

ifconfig -a
cat /etc/network/interfaces
route -n
cat /etc/resolv.conf

```

---

### Post by cariboo on 2009-01-13
Open an Applications-->Accessories-->terminal and type the following:

```
ifconfig
```

and 

```
cat /etc/network/interfaces
```

and paste the output of both commands in your next post.

Jim

---

### Post by RuleMaker on 2009-01-13
Firs of all thank you for such a quick reply and your will to help.
But after my provider fixed the router and I restarted my PC everything seems to work fine.
Sorry for fake alarm.

---

### Post by dcstar on 2009-01-13
> **RuleMaker said:**
> Firs of all thank you for such a quick reply and your will to help.
But after my provider fixed the router and I restarted my PC everything seems to work fine.
Sorry for fake alarm.

Please read my sig.

PS, Don't worry about it for now, I've just discovered that the "Solved" tool has been disabled so they can see how stable the forums are now (after they were brought back on-line).

---


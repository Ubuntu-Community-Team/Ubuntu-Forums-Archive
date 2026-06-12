---
title: "Two GDM instances ??"
date: 2008-05-15
forum: Desktop Environments
---

### Post by dushkal on 2008-05-15
Hello,

I recently observed that whenever I start the laptop, two instances of X are started alongwith 2 GDM instances. Can someone tell me why the second instance is started? I did a fresh install of HArdy Beta (now upgraded to release) but copied my home directory in order not to lose my customizations and private files, can this be related to that?

```
$ ps -ef | grep -i gdm
root      5435     1  0 07:59 ?        00:00:00 /usr/sbin/gdm
root      5442  5435  0 07:59 ?        00:00:00 /usr/sbin/gdm
root      5453  5442  3 07:59 tty7     00:19:06 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5720  5453  0 07:59 tty7     00:00:00 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
dushkal  28815 17483  0 17:19 pts/0    00:00:00 grep -i gdm
```

---

### Post by Dr Small on 2008-05-15
That is odd. For one reason, X server can not live twice (or more) on the same display (:0), so I don't even see how this is possible.

---

### Post by dushkal on 2008-05-16
> **Dr Small said:**
> That is odd. For one reason, X server can not live twice (or more) on the same display (:0), so I don't even see how this is possible.

That's the reason I was stumped too...anyone? I checked gdm.conf but there is nothing which could point out to this....

---

### Post by Dr Eigen on 2008-05-17
> **dushkal said:**
> Hello,
I recently observed that whenever I start the laptop, two instances of X are started alongwith 2 GDM instances.

+1

Fresh install, x86_64.  Everything works fine.  pstree (or looking at the ps output properly) shows they're spawning each other:
&#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg&#9472;&#9472;&#9472;Xorg
So I assume this is by design.

---

### Post by Oldsoldier2003 on 2008-05-17
Are you using the ati binary driver? Its a known bug using when the proprietary driver from ATI.

---

### Post by dushkal on 2008-05-19
Hi,

Thanks for the tip.

After disabling ATI binary drivers, the two instances of X stopped, but two instances of GDM are still there:
```

~$ ps -ef | grep gdm
root      5410     1  0 17:25 ?        00:00:00 /usr/sbin/gdm
root      5417  5410  0 17:25 ?        00:00:00 /usr/sbin/gdm
root      5424  5417  1 17:25 tty7     00:00:01 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
dushkal   6058  6045  0 17:26 pts/0    00:00:00 grep gdm

```

---

### Post by whereisian on 2008-11-20
I'm using Ibex. 

I disabled the ATI proprietary driver and rebooted. Now only 1 instance of gdm appears.

---


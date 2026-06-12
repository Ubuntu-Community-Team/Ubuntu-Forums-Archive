---
title: "Issue while booting"
date: 2009-05-09
forum: General Help
---

### Post by sanketvaidya on 2009-05-09
HI ALL,

OS is UBUNTU 8.10.  I have used UBUNTU for just above 3 months.

I am facing a strange problem while booting.

I get 

Starting Avahi mDNS/DNS-SD Daemon avahi-daemon   [fail]
After some time I get message related to 'hald'

*Starting* Hardware abstraction layer *hald* 
Boot process stops here for about 5 minutes.

Thereafter gnome login screen is displayed. But I cannot enter anything in login name using keyboard. Doing Alt + CTRL + F2 opens terminal & I am allowed to enter here from keyboard.

I just installed lokkit firewall before that. Could this be due to lokkit?

I disabled lokkit from recovery mode. But still problem persists. I even removed lokkit but still the problem persists.

Is there anyway to solve this issue without re-installing UBUNTU?

---

### Post by sanketvaidya on 2009-05-09
HI ALL,

OS is UBUNTU 8.10.  I have used UBUNTU for just above 3 months.

I am facing a strange problem while booting.

I get 

> **sanketvaidya said:**
>  Starting Avahi mDNS/DNS-SD Daemon avahi-daemon   [fail] 

After some time I get message related to 'hald'

> **sanketvaidya said:**
> *Starting* Hardware abstraction layer *hald* 

Boot process stops here for about 5 minutes.

Thereafter gnome login screen is displayed. But I cannot enter anything in login name using keyboard. Doing Alt + CTRL + F2 opens terminal & I am allowed to enter here from keyboard.

I just installed lokkit firewall before that. Could this be due to lokkit?

I disabled lokkit from recovery mode. But still problem persists. I even removed lokkit but still the problem persists.

Is there anyway to solve this issue without re-installing UBUNTU?

---

### Post by Peter09 on 2009-05-09
look through the log files

- initially look at the output from dmesg for errors  - post them here

```
dmesg | more
```

---


---
title: "SSH server keeps failing"
date: 2014-10-25
forum: Desktop Environments
---

### Post by Geoff_Lane on 2014-10-25
Hi folks,

I am running 12.04 with a stable system.

I have a friend in US who has 14.04 installed. She has ssh server running and I can log in using certificate so no password needed; I can access the desktop if need be using VNC via and ssh tunnel. 

I normally use it for command line access merely to transfer some shared videos but every few days (less than 24 hours recently) I cannot log in unless she reboots her computer.

Her computer seems OK, no lock ups, just can't use ssh until reboot.

Any ideas as to what the problem might be?

Geffers

---

### Post by Doug S on 2014-10-25
Is there any information in the logs files that might help. Check /var/log/*, particularly /var/log/auth.log. Is your friend running an iptables based firewall, and is there any chance that your IP address is getting blacklisted and / or restricted somehow?

Edit: Is sshd still running? Example:```
doug@s15:~/temp$ [COLOR=#ff0000]ps aux | grep sshd[/COLOR]
[COLOR=#ff0000]root      1603  0.0  0.0  61372  5460 ?        Ss   Oct20   0:00 /usr/sbin/sshd -D[/COLOR]
root      3061  0.0  0.0 272116 12784 ?        Ss   Oct20   0:00 sshd: doug [priv]
doug      3111  0.0  0.0 272256  6012 ?        S    Oct20   0:24 sshd: doug@pts/0
root     10223  0.0  0.0 272116 12656 ?        Ss   Oct22   0:00 sshd: doug [priv]
doug     10323  0.0  0.0 272256  5948 ?        S    Oct22   0:01 sshd: doug@pts/2
root     25816  0.0  0.0 272116 12664 ?        Ss   Oct23   0:00 sshd: doug [priv]
doug     25914  0.0  0.0 272256  6104 ?        S    Oct23   0:01 sshd: doug@pts/4
doug     31751  0.0  0.0  11756  2128 pts/4    S+   13:25   0:00 grep --color=auto sshd
```

---

### Post by Geoff_Lane on 2014-10-25
> **Doug S said:**
> Is there any information in the logs files that might help. Check /var/log/*, particularly /var/log/auth.log. Is your friend running an iptables based firewall, and is there any chance that your IP address is getting blacklisted and / or restricted somehow?


She has a router but a port redirect was set up to the Ubuntu machine which has a fixed local IP address.

Strangely it'll work fine for 2 or 3 days then wont connect unless machine is rebooted.

Was thinking of the 'keep alive' option but I seldom stay connected for too long anyway; perhaps an occasional restart of the ssh server via a crontab maybe, I am not too familiar with setting that up but maybe an option.

Geoff

---

### Post by bashiergui on 2014-10-26
Fixed local IP. But is the Internet-facing IP static?

---

### Post by Geoff_Lane on 2014-10-27
> **bashiergui said:**
> Fixed local IP. But is the Internet-facing IP static?

Yes, public IP address is static.

Geffers

---


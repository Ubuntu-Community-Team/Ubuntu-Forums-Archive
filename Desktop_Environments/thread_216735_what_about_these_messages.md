---
title: "what about these messages?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by tefflox on 2006-07-16
> Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[3338])
 
** and**

>  Checking `z2'... user root deleted or never logged from lastlog! 
** how do i follow up on these messages?**

---

### Post by T700 on 2006-07-16
Some context would be helpful.  What is generating these messages?  What's going on with your system?

Paul

---

### Post by tefflox on 2006-07-16
they're messages from 'chkrootkit'.  how can i detect packet sniffing?

---

### Post by ardchoille on 2006-07-16
> **tefflox said:**
> ** and**

 
** how do i follow up on these messages?**

These messages are output from using chkrootkit to check for rootkits.
I have used Linux for years, also used chkrootkit for quite a while. I am also a security zealot and my system is as closed off as I can get it while still being able to use things like Firefox and Thunderbird. I use both rkhunter and chkrootkit (along with tripwire and a few others) and I have always received your two messages when using chkrootkit in Ubuntu.. as well as a couple other distros.

This message:
```

Checking `z2'... user root deleted or never logged from lastlog!

```
tells me that you are using sudo and you have never actually logged in as root user on the system. That is a good thing.. keeping the root account disabled and using sudo :)

I have received the first message also but I am not sure what it means as I am still learning about TCP/IP, but I have seen this message on a lot of distros using chkrootkit. I don't, however, think either message is anything to worry about.

---

### Post by tefflox on 2006-07-16
do you know how to detect packet sniffing? ---and thanks for helping

---

### Post by ardchoille on 2006-07-16
> **tefflox said:**
> do you know how to detect packet sniffing? ---and thanks for helping

Unfortunately, no, I am still learning about that stuff.
I am wondering if that question would be good in its own thread, can't hurt anything.

---


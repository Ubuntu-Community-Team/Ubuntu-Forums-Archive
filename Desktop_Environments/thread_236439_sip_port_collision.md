---
title: "sip port collision"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Dr. Cox on 2006-08-14
hi there,

i've just started to use voice over ip applications starting with skype; then, having noticed that skype for linux doesn't support video i found the open wengo project; 

i installed the software as well. now, skype works, ekiga as well but the openwengo-client tells me, that the necessary sip-port was allready used by some oter application.

1) what are sip-ports
2)where do i find who is using which sip port
3) can't it be shared as to: only one app is open an running only. why does it think the other application that also uses this port is using it while it is off?

i hope to find some help as i 've run out of ideas
by the way, i'mrather new to linux.

thanks in advance for all the help

---

### Post by yugo on 2006-09-04
ekiga is also a sip softphone, so using the port 5060 UDP.
Try to change this port in the configuration window of wengophone

---

### Post by _asc_ on 2006-11-24
I have the same problem. I have tried to change the port a couple of times but no improvement. Has anybody solved this problem? 


BTW, I'm running Edgy.

---

### Post by glenndavy on 2007-01-25
> **Dr. Cox said:**
> hi there,


i installed the software as well. now, skype works, ekiga as well but the openwengo-client tells me, that the necessary sip-port was allready used by some other application.


hi there  Dr Cox
If its any consolation I get this issue too - i downloaded the openwengo2 client and it doesnt do this - im pretty sure it an issue in that client.

> 

1) what are sip-ports

FYI if you check /etc/services - you can find a list of most common ports - sip is 5060. Theres one of these files in windows too IRC, but not sure where it is.

> 

2)where do i find who is using which sip port

I think fuser sip/udp should do it? - but i suspect you wont find anything - like i said, i think the issues the client.


hope this helps

---


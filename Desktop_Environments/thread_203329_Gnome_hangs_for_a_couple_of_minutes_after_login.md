---
title: "Gnome hangs for a couple of minutes after login"
date: 2006-06-25
forum: Desktop Environments
---

### Post by manup on 2006-06-25
Hi,

This seems to be a common problem (as far as I read in the newsgroups) but no solution ever given. Even the cause seems to not to be clear. Well, here is my case:
1. Latest ubuntu and gnome and so on (25th June 2006)
2. After logging in the desktop background is displayed and nothing happens for a few minutes
3. During this wait I decided to look for open tcp connections, which is a common cause for waits, so this is the result of netstat -natp
--cut--
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 1 192.168.0.2:43406 127.0.0.1:16001 SYN_SENT 5614/gnome-session
tcp 0 1 192.168.0.2:43407 127.0.0.1:16001 SYN_SENT 5668/gnome-settings
---cut---
Other time I tried the port was 16000. Needless to say there is no service listening on that port. How can I disable this connection attempt? What should be listening on that port?

Thanks in advance,
Dimo

---

### Post by woedend on 2006-06-25
running wireless?  I thought it was fixed if so, but check out this thread - sounds similar - 
[http://www.ubuntuforums.org/showthread.php?t=158964&highlight=brown](http://www.ubuntuforums.org/showthread.php?t=158964&highlight=brown)

let me know your results

---

### Post by manup on 2006-06-25
I can now recall manually editing the /etc/network/interfaces file so that it connects to my home network with WEP, because the gnome und kde configurators did not succeed in doing that. I accidently commented out the loopback interface.... It is now solved :) 

Thanks for the fast reply!

Dimo

---


---
title: "gaim &amp; thunderbird - connection timed out"
date: 2006-10-03
forum: Desktop Environments
---

### Post by {spitFire} on 2006-10-03
Hi all,
  I've been using Ubuntu Dapper on Dell E1505 successfully for the past two weeks. However, since yesterday I faced a strange problem. Gaim and Thunderbird stopped working. 
  Now whenever I try to use Gaim and Thunderbird, they keep on try to connect to the server and then finally time out.
  When I try 'netstat -a -p' on the console, I see the state of the two applications on the corresponding ports as SYN_SENT. I'm confused as to why the connections are not getting established. I rebooted the laptop and found that the resolvconf service was failing. But, firefox is running without a glitch. I updated resolvconf and now that is working perfectly. No errors during startup or shutdown. 
  Now where should I start digging for more info to diagnose the problem?

---

### Post by {spitFire} on 2006-10-03
I now found out that none of the applications other than firefox are able to connect to the internet :(

  What could be the problem?

---


---
title: "Understanding netstat output,"
date: 2009-05-13
forum: General Help
---

### Post by dingbat32 on 2009-05-13
Hello all :D
If this is not the appropriate section for a non ubuntu question, then apologies.

I have a linux device on my lan. I've noticed that ocasionally when I run the 'netstat' command, It seems as if someone is running a remote SSH session on the device.  The output is as follow, (including only the line I'm interested in).

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0    360 192.168.1.101:ssh       202.105.49.*:38954     ESTABLISHED
```The SSH port is being forwarded to this device so that I can access it remotely.

I assume that the above is something I should be worried about. What do you guys think?

Any info would be much appriciated.

Rgds,
D ;)

---


---
title: "Firefox Continuously Transfers 1.4Mbps Over Loopback"
date: 2009-07-03
forum: Desktop Environments
---

### Post by jlward4th on 2009-07-03
Sometimes my Firefox 3.5 process sits around talking to itself at around 1.4Mbps.  Any idea why?

Here is what I know:

"iftop -i lo" shows:
```
dos:54465                  => dos:4713                   1.40Mb  1.42Mb  1.42Mb
                           <=                               0b      0b      0b
dos:4713                   => dos:54465                  79.6Kb  80.4Kb  80.4Kb
                           <=                               0b      0b      0b
```

```
jamesw@dos:~$ lsof |grep 4713
firefox-3  4834     jamesw   83u     IPv4     685775              TCP dos:54465->dos:4713 (ESTABLISHED)

jamesw@dos:~$ lsof |grep 54465
firefox-3  4834     jamesw   83u     IPv4     685775              TCP dos:54465->dos:4713 (ESTABLISHED)
```

Maybe Firefox just gets bored and wants someone to talk to.  I'm not sure but this does seem strange.  Any ideas?

Thanks.

---


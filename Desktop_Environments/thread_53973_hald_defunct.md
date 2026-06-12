---
title: "hald defunct?"
date: 2005-08-02
forum: Desktop Environments
---

### Post by twowheeler on 2005-08-02
I have been trying to debug automounting on my hoary machine.  CDs and DVDs do not automount or start totem or whatever.  I noticed this however, immediately after booting up:

```
dan@ubuntu:~$ ps ax | grep hal
 7042 ?        Ss     0:00 /usr/sbin/hald --drop-privileges
 7781 ?        Z      0:00 [40-hal-hotplug-] <defunct>
 7785 ?        Z      0:00 [40-hal-hotplug-] <defunct>
 7787 pts/0    R+     0:00 grep hal
dan@ubuntu:~$
```

... so does this mean that hal has crashed?  

Any suggestions?

---


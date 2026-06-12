---
title: "DCOP servernot running"
date: 2005-09-11
forum: Desktop Environments
---

### Post by mokong on 2005-09-11
help,

   what happened is this whenever i log-in to kubuntu 5.04, 

  itwill stop on setting up inter-process communication ,

   then will give me an error /there was an error setting up inter-process communication for KDE the message returned by the system was
could not read network communication list  /home/edward/.DCOPserver_limux_o

pls check dcopserver progam is running

what happened is i was palying MUPEN then the game hanged/ itried ctrl+alt
backspace /that when the problem began

help 

ty,

---

### Post by mvaniersel on 2005-09-16
Just want to say: I have the exact same problem. I get the following mysterious error:

```

There was an error setting up inter-process communications for KDE. The message returned by the system was:
Could not read network connection list.
/home/martijn/.DCOPserver_bigcat012_0
Please check that the dcopserver program is running.
```


EDIT: I solved this problem by deleting .ICEauthority-l and .ICEauthority-c in the home dir, and chowing all hidden files in the home dir that were owned by root. Does that work for you too mokong?

---


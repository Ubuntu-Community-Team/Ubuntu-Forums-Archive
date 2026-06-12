---
title: "amaroK dcopserver"
date: 2009-02-17
forum: General Help
---

### Post by dwieeb on 2009-02-17
So...I click on amaroK and it gives me this error:
```
There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list. 
/home/daniel/.DCOPserver_carla__0

Please check that the "dcopserver" program is running!
```

I looked around, found a certain [topic](http://www.ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver ) and tried out the terminal code. This is what happened...

```
daniel@carla:~$ sudo chown -R daniel:daniel /home/daniel/.*
[sudo] password for daniel: 
chown: cannot access `/home/daniel/./.gvfs': Permission denied
chown: cannot access `/home/daniel/.gvfs': Permission denied
```

Tried replying to that topic, it said I didn't have permissions. IM SICK OF NOT HAVING PERMISSION...lol.

So I made a new topic here.

---


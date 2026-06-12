---
title: "Icecast cannot create listener socket."
date: 2006-06-05
forum: Desktop Environments
---

### Post by Hitetsu on 2006-06-05
Hi,

I'm trying to set up an Icecast radio for a game with a friend. Unfortunately I have almost finished it (I think) and I hit a snag.

When I try to run Icecast, I get the following problem.

[PHP]
tony@beng:~$ sudo icecast2 -c ~/.icecast2/icecast2_config.xml
Could not create listener socket on port 8000
Server startup failed. Exiting
[/PHP]

After looking to see if there was a way to check what was using (or what could be using) port 8000, I got the following output:

[PHP]tony@beng:~$ netstat -anp |grep :8000
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN     2374/icecast2
tony@beng:~$
[/PHP]

I just wondered if anyone could tell me why I can't actually run it.

Any help would be appreciated.

---

### Post by denkedran on 2006-06-05
try the following```
kill 2374
```
your icecast2 server is already running

---

### Post by Hitetsu on 2006-06-06
Thanks a lot!

Now I managed to restart it, thinking it might solve my other problem ( [http://ubuntuforums.org/showthread.php?t=189281](http://ubuntuforums.org/showthread.php?t=189281) ) but it didn't. Have you any idea's why?

Sorry for asking so many questions, but I'd love to be able to do this, not only for my friend, but because I'd generally like to know more about little things like this, I think it's fun sometimes just knowing how to do stuff like that :D

---


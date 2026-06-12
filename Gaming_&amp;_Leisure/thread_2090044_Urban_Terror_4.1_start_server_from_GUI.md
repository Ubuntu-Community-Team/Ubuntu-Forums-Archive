---
title: "Urban Terror 4.1 start server from GUI"
date: 2012-12-01
forum: Gaming &amp; Leisure
---

### Post by kblood on 2012-12-01
Hello,

I have installed Urban Terror 4.1 from PlayDeb.net, and the game runs quite well.

I want to have a quick game every now and then with a friend, just 1 on 1, but I can't get the server to start!

I open Urban Terror, click on "Start Server", choose my options, and then I'm in. I can run around the map, shoot stuff, etc, works great.

But then, if I check, there is no open port! So of course, my friend, on a different computer in the same network, can't join my server.

See here:
```
root@computer:~# netstat -plant | grep LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1016/cupsd      
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      8752/dropbox    
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1407/dnsmasq    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      896/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      1016/cupsd      
tcp6       0      0 :::22                   :::*                    LISTEN      896/sshd        

```

Any ideas? Has anyone had this problem? For quick games I really don't want to start figuring out how to run a standalone server, but I guess that's maybe my only option?

Thanks!

---

### Post by kblood on 2012-12-01
Alright, forget it. Urban Terror, of course, is a UDP server, so it doesn't show on that list.

:oops:

---


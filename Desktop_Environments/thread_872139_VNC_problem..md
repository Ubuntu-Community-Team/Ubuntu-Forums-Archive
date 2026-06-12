---
title: "VNC problem."
date: 2008-07-27
forum: Desktop Environments
---

### Post by Underpants on 2008-07-27
Running a new 8.04 installation. 
This is a task I almost always do to new installations for remote access (I'm a network engineer/consultant, so I set up lots of boxes!)

Anyway, I like to have access to the console session at any given time (session 0, I suppose) 

So here is what I think I've always done. I must be missing something, because it isn't working this time around.

add this line
```
/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg
```

to 
```
/etc/gdm/Init/Default
```

Then connect and tunnel the session over ssh, and it just works. 


But this time, I've edited the file, restarted the computer, and I can connect to the login screen, enter my username and password, and then it drops the VNC connection. I try to reconnect and cannot. TightVNCviewer just says "connection closed" immediately after I try to connect.

Thoughts? What am I missing? What can I check?

---

### Post by krunge on 2008-07-27
> **Underpants said:**
> 
But this time, I've edited the file, restarted the computer, and I can connect to the login screen, enter my username and password, and then it drops the VNC connection. I try to reconnect and cannot. TightVNCviewer just says "connection closed" immediately after I try to connect.

Thoughts? What am I missing? What can I check?

GDM kills all X clients (including x11vnc) right after the user logs in.  You need to set ```
KillInitClients=false
``` in a gdm.conf file.

Details here: [http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager")

---

### Post by Underpants on 2008-07-27
That was it. 

thanks!

---


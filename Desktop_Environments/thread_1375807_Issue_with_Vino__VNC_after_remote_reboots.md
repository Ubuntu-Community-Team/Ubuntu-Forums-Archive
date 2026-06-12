---
title: "Issue with Vino / VNC after remote reboots"
date: 2010-01-08
forum: Desktop Environments
---

### Post by SeanConwell on 2010-01-08
Recently installed a new server with Ubuntu server 9.10 x64. Needed a desktop environment on it so I installed Gnome, which works fine. The only issue is that if the server is rebooted remotely, Vino won't start up for VNC connections until after someone physically at the server logs in.

I have webmin installed and working, so I can access the server that way, but need VNC working as well. Is there any way that through Webmin I can get gnome to log in and thus vino will start working? Is there some other VNC service I can install instead of the included Vino that will start up and work before a user actually logs in? Any suggestions on how to make it so VNC works after a remote reboot are much appreciated.

---

### Post by mocho on 2010-01-13
I had the same problem and of not being able to vnc to gdm and the old trick of adding 
```

/usr/lib/vino/vino-server &
```

to /etc/gdm/Init/Default before seemed to do nothing. after many time trying to find a solution I am now able to connect to vino vnc server (not sure if it was allowing vnc from the root account).
 

But now i cant remote vnc login because in gdm it asks for user permission (some one with physycal access to machine).

As I was writing i find the answer

In the GDM login when its asking for user to accept remote conection click on the remote desktop icon and enable it from there.

---

### Post by chitresh4u on 2010-01-18
@ SeanConwell
check following link for VNC login at GDM:
[http://flukylogs.blogspot.com/2009/11/setting-up-vnc-for-gdm-login.html](http://flukylogs.blogspot.com/2009/11/setting-up-vnc-for-gdm-login.html)

@ mocho
I am not able to get vino-server login in karmic and I do not want to enable root login. Is there any workaround?

---


---
title: "Exporting X Display issue"
date: 2006-02-27
forum: Desktop Environments
---

### Post by chromiumferret on 2006-02-27
Hi,
I'm trying to export my display from my ubuntu system to my Solaris 9 system.  I'm having no luck.  
When I log into the Solaris system, I do the following:


c6404@rdcapp01:~$ export DISPLAY=ralnx01:0.0
[1]+ Done xclock
c6404@rdcapp01:~$ xclock &
[1] 16654
c6404@rdcapp01:~$ Error: Can't open display: ralnx01:0.0

[1]+ Exit 1 xclock


I've tried it with IP address and hostname, but I get the same result.  I ssh over to the system and I've tried most of the ssh configuration tricks I've seen here.
One extra bit of weirdness.  On the localhost, if I try to change the display variable from :0.0 to localhost:0.0 and then attempt to launch xclock, I get the same error.  
I'm sure i've bollocksed up some setting, so if one of you big brains out there could give a hand, I'd appreciate it.  \\:D/

---

### Post by schilcha on 2006-02-28
Try using xhost to allow remote access to your X-server.

So, for the localhost-issue, I need to do the following: 
```

export DISPLAY=localhost:0.0
xhost +local:

```

For forwarding apps from remote machines, try
```

xhost +remote.host

```
on the maching you're sitting in front of.

It seems strange, that X-forwarding through your ssh-tunnel does not work. Did you use "ssh -X"? Is there a chance that X11-forwarding is forbidden on the sshd of the remote host?

---

### Post by wrtrdood on 2006-02-28
You also have to remove the *-nolisten tcp* parameter from (I think it is) the /etc/X11/xinit/xserverrc file.

---


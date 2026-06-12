---
title: "Cannot use Gnome apps remotely via X11 over ssh unless logged in on local terminal."
date: 2009-12-17
forum: Desktop Environments
---

### Post by hydrogen18 on 2009-12-17
Hi. I have a core i7 machine running ubuntu 9.10. It's mostly a home server and media center. Whenever I had 9.04 on it, I would regularly ssh back into the machine and extend X11 to my laptop(or whatever machine I was using) in order to use applications remotely. I can still ssh in and extend X11 to my local terminal no problem. Programs like wine, synaptic, etc. work fine. But I cannot get nautilus, gedit or lots of other gnome apps to work unless I am logged in with the same user I am using over ssh on the servers local terminal. It doesn't matter if I am using a linux client or a windows client with Xming. I get the same error in my terminal:

```

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-5Hu5GFRmWb: Connection refused)

```

Any idea on how to resolve this?

---

### Post by tux821 on 2009-12-17
Yes, just google your error message, many hits on this one, for example:

[https://answers.launchpad.net/ubuntu/+source/gconf/+question/51996](https://answers.launchpad.net/ubuntu/+source/gconf/+question/51996)
[http://forums.freebsd.org/archive/index.php/t-4803.html](http://forums.freebsd.org/archive/index.php/t-4803.html)
[http://forum.mandriva.com/viewtopic.php?t=93858](http://forum.mandriva.com/viewtopic.php?t=93858)

Please post back which solution worked for you..

---

### Post by hydrogen18 on 2009-12-31
Yes, I have already exhaustively searched google for a resolution to this issue to no avail. Any other ideas?

---

### Post by tux821 on 2009-12-31
Hmm, the difference with your issue compared to the others I found is that you have a workaround using the same user login name on server and client.

On other threads, like
[http://ubuntuforums.org/showthread.php?t=985509](http://ubuntuforums.org/showthread.php?t=985509)

sudo nautilus

Seems to make nautilus work.

So just to get this correct:

1) You want to login on your server on a normal user account for a Gnome/X11 session from any client machine (windows, Linux) using Xming over ssh?

2) On the above thread they found that NX Client/Server worked, can you try that?

---

### Post by hydrogen18 on 2010-01-04
1) Yes. Not specifically Xming as my local X server, I just use that while I am under Windows 7

2) It seems massive overkill to use something like that when X over ssh is a proven technology.

---

### Post by tux821 on 2010-01-05
> **hydrogen18 said:**
> 
2) It seems massive overkill to use something like that when X over ssh is a proven technology.
Agree.
The only reason I would use this NX Client / server may be for performance or extra features like sound.
So let's skip this workaround, you seem to have your own workaround using the same user login on client and server.

My guess it's some kind of Gnome access rights issue.
Personally I would Google and read posts to solve this.

For now I have no time (and no Windows 7 ;) to test this issue.  
So to be honest can't help you any further at the moment (sorry).

---

### Post by Docaltmed on 2010-01-05
I had a similar problem. NX was the only solution I found. I agree that it's overkill, but it gets the job done.

---


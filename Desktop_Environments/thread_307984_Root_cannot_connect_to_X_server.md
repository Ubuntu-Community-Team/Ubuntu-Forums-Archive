---
title: "Root cannot connect to X server"
date: 2006-11-27
forum: Desktop Environments
---

### Post by nofrak on 2006-11-27
I'm running an almost brand new installation of Kubuntu Edgy, and when I run graphical programs as root, it's giving me errors when I use sudo and refuses to connect at all when I'm using a root shell (su).  Here's an example using sudo:
```
oliver@ops:~$ sudo kate
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-4755' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

```
This doesn't seem to reduce functionality, but it is hardly encouraging.

Using su I get this:
```
root@ops:~# kate
kate: cannot connect to X server

```
At which opening the program simply fails.  

I have a modified xorg.conf to enable AIGLX, but my X server is still 0:0, so I don't think that should be a problem.  I don't necessarily mind using text-based programs, but I think there should be a fix or workaround for a problem like this.  Any help would be appreciated.

---

### Post by taurus on 2006-11-27
```

oliver@ops:~$ kdesu kate

```

---

### Post by gogo_mek on 2007-10-20
i am having the same problem. any solutions??

---

### Post by Elliot Li on 2007-10-21
The reason is that X server forbids root to connect, run this:
```
$ DISPLAY=:0.0 xhost +
```
They you should be able to run GUI program as any user on this system.

---

### Post by MeanderingCode on 2007-10-21
> **Elliot Li said:**
> ```
$ DISPLAY=:0.0 xhost +
```

Does this persist across shutdown/startups?  Does this apply to all users?
I'm trying to sudo as another non-root user and getting the same results as the OP.

Thanks.

---

### Post by Zamboniman on 2007-10-22
taurus already gave the solution above.  On kubuntu use kdesu instead of su, or kdesudo instead of sudo.  On ubuntu it's gksu and gksudo.

---

### Post by MeanderingCode on 2007-10-22
> **Zamboniman said:**
> taurus already gave the solution above.  On kubuntu use kdesu instead of su, or kdesudo instead of sudo.  On ubuntu it's gksu and gksudo.

Are you refferring to my question?
I have kdesu, but my system shows (in the path) a kdesud, not kdesudo.  When i man it, i get the kdesu man page, when i whatis, it tells me "runs a program with elevated priveledges."
When i run it, it sits in the background and goes nowhere, command passed as argument or not.

What's going on there?  How can i fix it?

---

### Post by Elliot Li on 2007-10-23
> **MeanderingCode said:**
> Does this persist across shutdown/startups?  Does this apply to all users?
I'm trying to sudo as another non-root user and getting the same results as the OP.

Thanks.

This doesn't survive reboot. While this do apply to all users on this system. HTH.

---


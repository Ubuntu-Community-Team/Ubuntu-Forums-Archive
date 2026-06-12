---
title: "shutting down machine from windowmaker"
date: 2009-05-26
forum: Desktop Environments
---

### Post by phonky on 2009-05-26
Hi,

I am using windowmaker on top of xubuntu on a box from 2001.
Thanks to this conf, my box is flying ;)

However, I'd like to make my happiness complete by being able
to shutdown the machine from wmaker.
I always have to open a terminal, and type 
```
sudo halt
```.

With the same user, with LXDE as loaded DE, I can shutdown the machine.
I installed a little app called wmShutdown, but clicking on the
"halt" or "reboot" button has no effect.

Must be some permission issue(?).

Suggestions?
Any and all help appreciated.

---

### Post by phonky on 2009-05-27
Solved. 

There is a small applet called wmShutdown for WindowMaker which adds a little app on the dock on the desktop. I had it installed already, but clicking on either "halt" or "reboot" did nothing.

I hadn't read the man page of it. There it says
> To read more you should look into /usr/share/doc/wmshutdown.

Well, there is a README.debian, where it says
> After installation you have to set suid at /sbin/shutdown, 
You can do this by chmod +s /sbin/shutdown

That's what I did and now it works ;)

Questions however:
1) What does 
```
chmod +s /sbin/shutdown
``` really do?
man chmod says
>  set user or group ID on execution (s)
Does that mean my user id is set when executing /sbin/shutdown?

2) Is there any security issue on this? I'm on a single user machine, I don't think here (?), but sure on a multi-user machine or on a server you wouldn't do that.

---

### Post by phonky on 2009-05-27
Another (better) solution:

edit /etc/sudoers to include a line
to allow a specific user (I am using group) to
allow NOPASSWD for /sbin/shutdown

---


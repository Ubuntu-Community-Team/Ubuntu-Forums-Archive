---
title: "PLEASE HELP ME STOP ssh-agent"
date: 2006-08-14
forum: Desktop Environments
---

### Post by harisund on 2006-08-14
I have been trying out various ways to stop the silly SSH-agent from running every time i login. A ps axjf listing results in 

```



    1  4523  4523  4523 ?           -1 Ss       0   0:00 /usr/sbin/gdm
 4523  4539  4539  4523 ?           -1 S        0   0:00  \_ /usr/sbin/gdm
 4539  4549  4549  4549 tty7      4549 Rs+      0   0:30      \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 4539  5025  5025  5025 ?           -1 Ss    1000   0:00      \_ x-session-manager
 5025  5067  5067  5067 ?           -1 Ss    1000   0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager

```

So basically the ssh-agent is started by the x-session-manager. 

The x-session-manager is none other than gnome-session, which in turn starts everything found in /usr/share/gnome/default.session. But ssh-agent is not there!

How on earth do I stop it?

---

### Post by kebes on 2006-08-14
I think "ssh-agent" appearing as part of "x-session-manager" is quite normal. The usual way to remove the ssh-server daemon (which I assume takes ssh-agent out as well) is to go:
```

sudo /etc/init.d/ssh stop

```

(You can use "start" instead of "stop" later to start it again.)

Of course the above will stop the ssh server from running, so that service will be completely disabled. Is that what you wanted?

---

### Post by harisund on 2006-08-14
First, I don't have a SSH server installed. So naturally, /etc/init.d/ssh isn't going to work, since there exists no file titled 'ssh' in my /etc/init.d/ directory. 

Second, ssh-agent has nothing to do with a SSH server being installed. A SSH server allows other machines to login to this machine, and ssh-agent 'remembers' passphrases for password-less access to other machines. Kind of like a keyring daemon

---

### Post by ardchoille on 2006-08-14
> **harisund said:**
> I have been trying out various ways to stop the silly SSH-agent from running every time i login. A ps axjf listing results in 

```



    1  4523  4523  4523 ?           -1 Ss       0   0:00 /usr/sbin/gdm
 4523  4539  4539  4523 ?           -1 S        0   0:00  \_ /usr/sbin/gdm
 4539  4549  4549  4549 tty7      4549 Rs+      0   0:30      \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 4539  5025  5025  5025 ?           -1 Ss    1000   0:00      \_ x-session-manager
 5025  5067  5067  5067 ?           -1 Ss    1000   0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager

```

So basically the ssh-agent is started by the x-session-manager. 

The x-session-manager is none other than gnome-session, which in turn starts everything found in /usr/share/gnome/default.session. But ssh-agent is not there!

How on earth do I stop it?

Here's what I did to keep ssh-agent from running at login:

1. gksudo gedit /etc/X11/Xsession.options
2. Find that line that says: use-ssh-agent
3. Change that line to read: # use-ssh-agent
(this is just commenting out that line so the x session ignores it)
4. Save the file, log out and back in and ssh-agent shouldn't be running anymore upon login.

Hope this helps.

---

### Post by harisund on 2006-08-14
ardchoille, YOU ARE GOD! Thank you so much. 

Unfortunately, I am not done here. Please see my latest post on different gnome startup options. Though I must say, thanks a real ton.

---

### Post by ardchoille on 2006-08-14
> **harisund said:**
> ardchoille, YOU ARE GOD! Thank you so much. 

Unfortunately, I am not done here. Please see my latest post on different gnome startup options. Though I must say, thanks a real ton.

Thanks, just helping as much as I can :)
Which thread is it? Got a URL? I'll try to help with it :)

---

### Post by harisund on 2006-08-14
Right here, in the desktop support thread. 

Haven't I seen your nick in the #ubuntu as well?

---

### Post by ardchoille on 2006-08-14
> **harisund said:**
> Right here, in the desktop support thread. 

Haven't I seen your nick in the #ubuntu as well?

Indeed you have seen my nick in #ubuntu, I hang out there and help as much as I can there too. I enjoy helping people with this awesome distro :)

You said you had another question. What is it? I think I may have missed it somewhere.

**EDIT:** Nevermind, I see it.

---

### Post by harisund on 2006-08-14
[http://ubuntuforums.org/showthread.php?t=236523](http://ubuntuforums.org/showthread.php?t=236523)

Thanks again.

---

### Post by troythered on 2006-11-18
So why is ssh-agent started up at all?  Surely the developers included it for some reason?  I'd like to know

Troy

---

### Post by harisund on 2006-11-20
troythered, I have no clue and that is one of the reasons that Ubuntu annoys me. Ubuntu is, yes, near perfect, everything works and all hardware is recognized. However, once you move up from the level of "dumb, beginner user" to a "power user" and you want to customize your machine to a greater extent than merely changing the wall paper, you begin to see how bad Ubuntu is at documentation, and how as long as you agree with the developers' ideas everything is good, and how hard it is to go against what the developers wanted us to have .

---


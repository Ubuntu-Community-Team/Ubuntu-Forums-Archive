---
title: "No GUI with 7.04 server - yikes"
date: 2007-05-31
forum: Desktop Environments
---

### Post by ear-lution on 2007-05-31
I've just installed festy fawn (to replace Win2k3), have very very little Linux experience and after installation was presented with a very useful command prompt and something about sudo.

I literaly have no idea what to do next, how do I get a GUI up so I can get on with setting-up/learning the system?

TIA

---

### Post by aysiu on 2007-05-31
The server isn't supposed to have a GUI. If you must have a GUI to function, or if you actually intended to have a home desktop (as opposed to a server), this may help:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by cantormath on 2007-05-31
> **ear-lution said:**
> I've just installed festy fawn (to replace Win2k3), have very very little Linux experience and after installation was presented with a very useful command prompt and something about sudo.

I literaly have no idea what to do next, how do I get a GUI up so I can get on with setting-up/learning the system?

TIA

Alright, it sounds like you installed the 'Server Edition'.  You should have installed the desktop cd, not the server.  I would suggest reinstalling with the Desktop CD.  You can still do all the server stuff, it just comes with the gui as well.

if you would rather install the gui.......you can with
```

:~$ sudo apt-get update
:~$ sudo apt-get install ubuntu-desktop

```hit y when prompted.

I would also, before doing the above command, update the system.  
```

:~$ sudo apt-get update
:~$ sudo apt-get upgrade
:~$ sudo apt-get dist-update

```you should then reboot the machine, log back in and install the ubuntu desktop.

Hope that helps.

---

### Post by aysiu on 2007-05-31
You actually don't have to reboot the system (although that'll work, too). You can just do ```
sudo /etc/init.d/gdm start
```

---

### Post by cantormath on 2007-05-31
> **aysiu said:**
> You actually don't have to reboot the system (although that'll work, too). You can just do ```
sudo /etc/init.d/gdm start
```

I ment the reboot for the kernel update, in case there was one.
But you are absolutely right, sudo /etc/init.d/gdm restart will restart the gui, I should have mentioned that.:)

---

### Post by aysiu on 2007-05-31
Ah, good point. There probably would be a kernel update.

---


---
title: "Karmic: boots to terminal, delay, then GDM"
date: 2010-02-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by calvin mitchell on 2010-02-16
When powering on an Inspiron 1501, machine boots to terminal line, asks for login info, stays at terminal after login for approximately 30 seconds, then loads GDM.

On initial install upgrade (fresh install) of 9.10, I didn't experience this problem.  After several days of use (10-15 boot sessions) I started to have this problem.

Help?

---

### Post by lz1dsb on 2010-02-18
I've also noticed something similar in my setup. I have a Dell Studio 1555 running Ubuntu 9.10 on it. But in my case I guess it's because I've added additional application and panel applets which are loading during startup. So did you added any additional applications at startup? Do you have any applets loading during startup?

Cheers, 
Boyan

---

### Post by veko on 2010-02-18
> **lz1dsb said:**
> I've also noticed something similar in my setup. I have a Dell Studio 1555 running Ubuntu 9.10 on it. But in my case I guess it's because I've added additional application and panel applets which are loading during startup. So did you added any additional applications at startup? Do you have any applets loading during startup?


What sorts of applications you have on startup?

My Ubuntu 9.10 on Dell Studio 1555 starts up just fine, regardless that I too have some additional startup and panel applications. They are pretty small though, and don't take too long to start.

However, I have a small problem on shutdown: instead of the graphical shutdown screen I get a text login, and then a message about usplash shutting down appears. The computer actually shuts down after couple of seconds, so this is merely an aestetic glitch, but annoying nevertheless.

---

### Post by lz1dsb on 2010-02-19
Well, nothing much. Frankly I've never measured the boot time exactly. I think in the beginning it was less than 50 seconds. Now after enabling an emerald window theme I noticed that on start up it takes a little bit longer. 
I also haven't seen this graphical shutdown screen on my laptop and get those text messages. I've only seen that shutdown screen on the virtual machine with Ubuntu 9.04 that I'm running here in the office.

Cheers,
Boyan

---

### Post by lz1dsb on 2010-02-19
Yeah, I forgot. I also have the netspeed and system monitor applets.

---

### Post by calvin mitchell on 2010-02-21
No. I don't have any applets that run.  I did turn off some of the services that Ubuntu loads by default on startup.  I disabled the CUPS and bluetooth services since I don't use them.  I didn't make any other modifications to the default boot sequence.

Not sure what to do.  Is there a boot log that would be helpful for me to review to see where the stall is?

---

### Post by lz1dsb on 2010-02-23
So in your estimation how much has the boot time increased? I'm just interested. 
It is possible to log tough what's happening to the system while booting. But because the boot log is disabled by default, you need to enable it and then restart to collect the logging information. There's a nice old thread about this:
[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)
You can upload the logs than so that we could all see what's happening with your system while booting.

Cheers, 
Boyan

---


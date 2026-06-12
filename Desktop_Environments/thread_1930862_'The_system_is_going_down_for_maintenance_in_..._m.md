---
title: "'The system is going down for maintenance in ... minutes' login incorrect"
date: 2012-02-24
forum: Desktop Environments
---

### Post by lamb0 on 2012-02-24
Dear all,

On my Kubuntu 11.10 x64 I always use the ```
sudo shutdown hh:mm -P
``` function when I go to sleep. One time somebody else did this for me and forgot something: -P. This resulted in the computer not shutting down so I turned it down just before the time that it would actually have done that if -P (power off) had been used.
When I now try to log in I get the warning 'The system is going down for maintenance in 4 minutes' and the only thing I can do is click OK. After that I get the normal login screen and after typing my pw it gives me the 'system is going down...' warning again. When I then click OK, I get 'login incorrect'. 
I get exactly the same stuff when I try to log in with Xorg disabled. The problem is that it is stuck at username@login: and there seems to be no way to type any command when not logged in.

Thanks in advance for the help.

---

### Post by youngunix on 2012-02-24
Are you trying to shut it down at a certain time, or just turn it off right away? if "right away" why not use: ```
sudo poweroff
``` it works like a charm.

Now, when you are at the login screen try this [[SIZE=2]**ctrl+alt+F1**[/SIZE]] (I'm not sure if it works on kubuntu but since it does on ubuntu, it should), it'll drop in a login shell (terminal), type in your login info then try to shut it down from there.

---

### Post by roelforg on 2012-02-24
> **youngunix said:**
> Are you trying to shut it down at a certain time, or just turn it off right away? if "right away" why not use: ```
sudo poweroff
``` it works like a charm.

Now, when you are at the login screen try this [[SIZE=2]**ctrl+alt+F1**[/SIZE]] (I'm not sure if it works on kubuntu but since it does on ubuntu, it should), it'll drop in a login shell (terminal), type in your login info then try to shut it down from there.
As the kernel handles that CTRL-ALT-F* it should be the same.

---

### Post by lamb0 on 2012-02-24
Yes I was actually trying to shut it down at a certain time. This failed since the '-P' was not included in the command but now I still get the 'login incorrect'. Even if I try to login via console with ctrl+alt+F1 it gives this error. It almost looks unrelated but since nothing else was changed I thought the power off was to blame for me not being able to log in.

---

### Post by ShawnKemp on 2012-08-26
I just ran into this same problem on Ubuntu Server 10.04.4. I think the problem may have been that I hit the power button before the scheduled shutdown was complete. Hard resets didn't help, but I finally tried hitting Ctrl-Alt-Del. That prompted a clean reboot and after that I was successfully able to log in.

---


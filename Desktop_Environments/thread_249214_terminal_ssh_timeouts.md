---
title: "terminal ssh timeouts"
date: 2006-09-02
forum: Desktop Environments
---

### Post by cjraven on 2006-09-02
Does anyone has a quick answer to this?

I keep several ssh sessions open to various servers at work from my home (dapper) box *and* connect over sshfs to those same machines.

A common problem exists with both...after a certain time the session dies, whether it's a terminal session or an sshfs session.

Does anyone know of a "magic keep-alive" setting someplace which would stop this from happening in the future? It's most certainly not mission critical, just annoying when it happens, nothing more than that.

I've hunted around ssh documentation, thus far without success. Perhaps there's something else I'm missing

Regards & TIA,
-Colin

---

### Post by ayoli on 2006-09-02
check your /etc/ssh/sshd_config file do you have this line ?
```
KeepAlive yes
```
if not, tryto add it by editing file:
```
sudo gedit /etc/ssh/sshd_config
```
regards.

---

### Post by christhemonkey on 2006-09-02
EDIT: Its probably best you ignore this, saturday afternoons arent my best time...

Do you get your ip adress from DHCP?

if so, your lease may be expiring at an ill oppertune moment.

Maybe you should set your ip adress to static if this is the problem, or you should increase the lease time for the ip adress (if possible).

---

### Post by whizbaby on 2006-09-02
Perhaps servers are configured to kick out clients after a certain time of inactivity ? See admin if for this (of course only when the garlic-sauce stuff didn't work).

---

### Post by cjraven on 2006-09-02
> **ayoli said:**
> check your /etc/ssh/sshd_config file do you have this line ?
```
KeepAlive yes
```
if not, tryto add it by editing file:
```
sudo gedit /etc/ssh/sshd_config
```
regards.

Yup it was already in there. That was one of the items a bit of RTFM showed.
Thanks for a lightning fast response BTW!!! :D

---

### Post by cjraven on 2006-09-02
> **christhemonkey said:**
> EDIT: Its probably best you ignore this, saturday afternoons arent my best time...

Do you get your ip adress from DHCP?

if so, your lease may be expiring at an ill oppertune moment.

Maybe you should set your ip adress to static if this is the problem, or you should increase the lease time for the ip adress (if possible).

Good advice - Saturday afternoon or not!!
However - it's a static IP :D
-C

---

### Post by cjraven on 2006-09-02
> **whizbaby said:**
> Perhaps servers are configured to kick out clients after a certain time of inactivity ? See admin if for this (of course only when the garlic-sauce stuff didn't work).

Well, I'm almost embarassed to say this, but I'm the admin on the boxes in question, hence my constant connection to them - just in case staff members have a problem (which of course <splutter> never happens!!)

I'll wander through the ssh configs on the boxen concerned & see if I can determine is there is an inactivity setting someplace that could be tweaked.

This is a first, I used to connect from XP with Putty/Secure_CRT, both of which have a builtin keepalive setting to prevent this from happening.

The truly bizarre aspect of the problem is that my colleague - who deployed ubuntu at *his* home at exactly the same time - and who also connects to the same servers as I do, apparently never experiences this problem. This makes me point my suspicion finger at my DSL router, but maybe I'm only doing that because it's a sitting target and can't defend itself. ](*,)

---

### Post by ayoli on 2006-09-02
can't you borrow another DSL router to test if it's really the problem ?

---

### Post by whizbaby on 2006-09-02
Check if it's really server timeout problem (your colleague stays tuned so why should it? Only reason coming to my mind could be different working habits ) by ssh-ing there and then open an *emacs -nw* session. (this prevents me from being kicked out of university net)

---

### Post by RichJacot on 2006-09-02
Hello,

I've ran across this many many times when ssh'ing between different business units (all having their own firewalls).  

Is there a firewall between your client and server?  If so, its the firewall timing you out.  Firewall tcp timeout defaults are one hour, I believe.  One very simple work around I use is to a simple ping before the session sit idle.

ping -i 99 localhost

This will keep your session alive.

Let me know if this helps.

Rich

---

### Post by crispo on 2006-11-18
uhm i have exactly the same problem, any ssh connection disconnect after a certain among of time... also if i ssh from my laptop at home (LAN)...

---


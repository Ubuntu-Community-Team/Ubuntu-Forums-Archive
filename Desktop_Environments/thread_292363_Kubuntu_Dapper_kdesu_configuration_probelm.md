---
title: "Kubuntu Dapper kdesu configuration probelm"
date: 2006-11-03
forum: Desktop Environments
---

### Post by zytsef on 2006-11-03
I've been trying to get wireless assistant to run without a password for a regular user on a laptop recently. I've modified the sudoers file so it should be working, however whenever I start wireless assistant kdesu demands a password.  Feeding kdesu nothing starts it with serious restrictions.

How do I properly configure kdesu for the behaviour I want?
Many thanks.

---

### Post by trcook on 2006-11-04
I have the same problem. The man page for wlassistant suggests adding a %Wifi group (with some kind of no-password attribute)to the sudoers file  and then adding the users you want to be able to use wlassistant w/o a password to that group.

I suspect that you have tried that. I tried it also and was, like you, still prompted for a password. I tried simply running "sudo wlassistant" logged in as a user in the wifi group and the progam started but would not register with any wireless networks returning errors about insufficient permissions.

---

### Post by zytsef on 2006-11-07
Didn't think to look in the man pages. I'm not used to finding such useful and specific information there, just arcane syntax stuff. Anyway, the way I had my sudoers file accomplished the same thing as what the man pages suggest, and you're right, wlassistant still complains about insufficient permissions. 

I think the problem lies in the fact that kdesu is trying to use su to open wlassistant, which I haven't given the user access to, just root access to wlassistant through sudo. It's interesting to note that trying to run 'sudo wlassistant' from terminal results in ```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

wlassistant: cannot connect to X server :0.0
```
and exits. I'm not sure what to make of that.

---

### Post by zytsef on 2006-11-09
My script-fu isn't up to snuff but I found this, and it seems to work just the way I need it without sacrificing security... at least as far as I can tell.
[http://www.linuxquestions.org/linux/blog/w322/2006-09-09/Auto_connect_to_wireless_network_without_sudo_privileges](http://www.linuxquestions.org/linux/blog/w322/2006-09-09/Auto_connect_to_wireless_network_without_sudo_privileges)

---

### Post by pgroover on 2006-11-16
> **zytsef said:**
> My script-fu isn't up to snuff but I found this, and it seems to work just the way I need it without sacrificing security... at least as far as I can tell.
[http://www.linuxquestions.org/linux/blog/w322/2006-09-09/Auto_connect_to_wireless_network_without_sudo_privileges](http://www.linuxquestions.org/linux/blog/w322/2006-09-09/Auto_connect_to_wireless_network_without_sudo_privileges)

Thanks!!  I had written my own script to do the same but this one is "cleaner"! :D

---


---
title: "Auto-login on a command-line ubuntu"
date: 2008-12-16
forum: General Help
---

### Post by lardandweed on 2008-12-16
Hi! I'm running a base installation of ubuntu intrepid and i've setup autologin in this way

1) sudo aptitude install rungetty
2) sudo vim /etc/event.d/tty1
3) comment out "exec /sbin/getty 38400 tty1"
3) add line "exec /sbin/rungetty tty1 --autologin username"

just a couple of questions about this:

1) I've read that in previous revisions of ubuntu (more specifically, i was reading about dapper), the difference between aptitude and apt-get was that aptitude handles dependencies during uninstalls better than apt-get does. Is this still the case in intrepid and is there anything else that warrants the use of one over the other?

2) is there a way for me to setup auto-login without installing applications like rungetty? (yes, i know that auto-login is a breach in security but i'm not using this system for anything other than learning how linux works =p)

---

### Post by Polygon on 2008-12-16
question 1: there really is no difference between the two now, both handle dependencies fine now. i just prefer apt-get cause i know the synatx better and its easier to type =P

and there was another post on this issue and i think you need to install rungetty. you can always download the program off the web (search rungetty, intrepid on google and you should be able to find it on packages.ubuntu.com) and you can put it on a usb key and install it there if you do not have a working internet connection

---

### Post by lardandweed on 2008-12-16
okie dokes! thx a bunch for the clarification =p

---

### Post by IdentifyTarget on 2009-02-26
I tried the code from OP and got stuck at 'Running local scripts (/etc/rc.local) I eventually found this which worked.

```
exec /bin/login -f username
```

instead of 

```
exec /sbin/rungetty tty1 --autologin username
```

---

### Post by casey02 on 2009-10-25
I have follow both the recommendation, but still does not work !!

I am currently only has terminal access to the remote machine, but still cannot autologin !!

---

### Post by Bender2k14 on 2009-10-31
You could ssh with X forwarding and then use the GUI method to configure the auto-login settings.

---

### Post by DouglasAWh on 2010-10-12
> **IdentifyTarget said:**
> 
```
exec /bin/login -f username
```

Did you have to do the other stuff before that?  I added that (with my username) but it did nothing.

---


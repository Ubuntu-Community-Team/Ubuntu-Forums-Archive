---
title: "Which version for Dell Inspiron 700m?"
date: 2014-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Buntu Bunny on 2014-01-09
Dell Inspiron 700m
Xubuntu 12.04.3 

I only use this old laptop for wifi away from home. Yesterday I took it to the public library to update, but ran into a major problem after the updates, namely, I lost my graphical interface. (Solved, sort of, [that thread here]("http://ubuntuforums.org/showthread.php?t=2198358")). One of the things I learned from that conversation is that perhaps this is a problem with older Dells and Xubuntu 12.04.3.

```
startX
```

got the desktop back, but

```
sudo shutdown now
```

revealed more problems. The system wouldn't shut down.

```
modem-manager [3182]: Could not get the system bus. 
Make sure the message bus is running? Message: Failed 
to connect to socket /var/run/dbus/system-bus-socket: 
No such file or directory
root@buntubunny-Inspiron-700m: ~#
```

Yikes! At that point I had to go and pulled the plug. 

I stick with LTS because I want to avoid problems like this and am hoping a fix is imminent. However, it got me wondering if another Xubuntu version or Ubuntu flavor wouldn't be better for this old laptop. Suggestions?

---

### Post by Dennis N on 2014-01-09
I have Lubuntu 12.10 on the same laptop. It is dual boot with the Xubuntu 12.04 and is working fine. Very solid. You could try a dual boot setup and see how you like it. That way you don't have to decide now about Xubuntu. You don't need much disk space to do that. Just an idea.

The aformentioned problem with Xubuntu did not happen again in two boot ups yesterday. Your problem with the shutdown is something more. Has it reoccurred?

On the shutdown, rather than pull the plug, do you know about Alt+PrintScreen+REISUB? It is a safe reboot when all else fails.

Edit: Slight correction: it's Lubuntu 13.04 installed on there, not 12.10.

---

### Post by Dennis N on 2014-01-09
A short explanation on Alt+PrintScreen+REISUB:

[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

It also says in there using Alt+PrintScreen+REISUO will shutdown.

---

### Post by Buntu Bunny on 2014-01-09
Well, this time it booted right to the login screen. 
All options were available on the logout screen.
It shut down no problem. :confused:

I confess I didn't know about Alt+PrintScreen+REISUB. I knew there must be a safer way, but I had run out of library computer time and needed to get home. I'm going to keep a notebook with the laptop of all these codes!

I will definitely take a loot at the link, Dennis N. Will also take a look at Lubuntu. Thanks so much for all your help.

---

### Post by xSCCMx on 2014-02-01
Do it starting from lubuntu 12.04 (not an LTS) as the Inspiron 700/710m does not support booting PAE kernels...

---


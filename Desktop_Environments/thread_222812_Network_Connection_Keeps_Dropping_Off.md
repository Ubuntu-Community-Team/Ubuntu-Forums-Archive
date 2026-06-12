---
title: "Network Connection Keeps Dropping Off"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Ted_Smith on 2006-07-25
For some odd reason my connection to my router keep dropping off. I'll be working away surfing the net, then, all of a sudden Firefox just says 'Looking for .....' and eventually times out. 

I cannot ping the router either  - 100% packet loss. 

It's not the router becuase as soon as I reboot my PC it's fine again - sometimes for hours and sometimes just for a few minutes.

1) What could the problem be and how do I go about fixing it
2) With Linux, there must be an easier way of resetting the ethernet connection than rebooting the whole system (I have tried '/etc/init.d/ networking restart' but that does not work).

Thanks for your help

Ted

---

### Post by jrbush82 on 2006-07-25
Have you tried using the GUI configuration tools?  I believe it is something like System > Administration > Networking.

You may also check out the ubuntu dapper wiki for networking:
[http://ubuntuguide.org/wiki/Dapper#Networking](http://ubuntuguide.org/wiki/Dapper#Networking)

Verify that you are using the correct drivers for your network card, if not... that maybe causing your problems.

---

### Post by Ted_Smith on 2006-07-25
It's been fine for months - no problems at all - up for weeks at a time. So I know it's configured OK. And it works for a while after reboot, but then it just stops.

---

### Post by Ted_Smith on 2006-08-23
This is still happening. It is very frustrating. This evening, as an example, my PC had been on all day but with no one logged in. I sat down, logged in, and straight away, no connection. I rebooted, and I have a connection? What gives? 

Most importantly, how can I achieve what the reboot is achieving, without having to reboot? There must be a way of restarting the netwrok config without rebooting on a system like Linux?

---

### Post by Ted_Smith on 2006-08-29
Please can someone offer me some guidance here? 

It just keeps happening. Just now, I have been working happily for 2 hours, browsing the web using FF, sending and receiving e-mails with Thuinderbird, then all of a sudden, nothing. No connection. 

I reboot, and it's fine. 

Surely there must be a way of a) restarting the network connection without rebooting and b) a cause of the problem. If someone could provide an answer for point a) I'd be appreciative. 

Cheers

Ted

---

### Post by Ricky75 on 2006-08-29
Hi, I've been having exactly the same problem.  If you find an answer please post.

---

### Post by bbzbryce on 2006-08-29
I had a similar problem awhile back which affected my computer more so than my house mates Windows Boxes.  The problem was with to many connections on our router, and therefore it would essentially drop connections.

A common thing I did was: sudo dhclient 

This basically releases and renews your ip address.  It might save some reboots, but as to why your connection is dropping I am unsure.

---

### Post by fragos on 2006-08-29
> **Ted_Smith said:**
> Please can someone offer me some guidance here? 

It just keeps happening. Just now, I have been working happily for 2 hours, browsing the web using FF, sending and receiving e-mails with Thuinderbird, then all of a sudden, nothing. No connection. 

I reboot, and it's fine. 

Surely there must be a way of a) restarting the network connection without rebooting and b) a cause of the problem. If someone could provide an answer for point a) I'd be appreciative. 

Cheers

Ted

System-> Administration-> Networking-> select connection-> Deactivate button-> Activate button

---

### Post by mssever on 2006-08-30
> **Ted_Smith said:**
> I have tried '/etc/init.d/ networking restart' but that does not work
You've probably tried this, too, but I thought I'd ask anyway. Have you tried the above with sudo?

---


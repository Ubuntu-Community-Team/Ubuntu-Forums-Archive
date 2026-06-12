---
title: "Screen TCP Log Viewing Solution"
date: 2009-06-18
forum: General Help
---

### Post by tomehb on 2009-06-18
Need help creating a Log Viewing Solution for User....

I would like a user to be able to telnet to a port on a host - and to be able to view "screen" that is running in the background with four different subwindows/splits tailing four different files....

My Main question is... Is this possible? If so could anyone point me in the right direction...

---

### Post by t4thfavor on 2009-06-18
Sounds like a custom app to me, I know you can have a program execute on login for terminal users, so your first step would be to find a program that displays apps in a manner you want them to display.

So think of it like an 4 apps inside of an app.

That or you could teach the client how to switch between 4 screen windows after logging in with telnet. 

the latter sounds like a much easier solution.

---

### Post by jonobr on 2009-06-18
Hello


That question seems to be very high level,
Im wondering if you could break it down a bit.

Are you thinking of monitoring a machine that is in some location which needs to be monitored by you for errors or output?

What are trying to look for or tail?

There is a telnet client on ubuntu, but not a telnet daemon by default so you would typically use ssh to connect to another machine, although nothing is stopping you telnetting once your install or start the telnet daemon.


Once in with your session, either telnet or ssh,
what are you trying to tail,
what files are you looking for?

If you looking to tail certain files, could you not open four sessions to that one machine?

If your looking to get some specific statistics from that machine you should considering monitoring the system remotely with something thats designed for that purposes, like SNMP, where you could set up polling to a machine to get the information you want

lastly

Im assuming you are a valid or trusted user on that remote computer, so there is no issues of privacy invasion.

---


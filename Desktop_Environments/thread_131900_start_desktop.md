---
title: "start desktop"
date: 2006-02-17
forum: Desktop Environments
---

### Post by Eloise on 2006-02-17
Now that I've installed it, how do I get to the desktop?

just installed 5.10 on an old Toshiba Satellite 4000, 233 Mhz, 160 mb RAM, 4.1 gig hard drive. It appears to install OK (I ordered a CD after I had a similar problem with a downloaded version). I installed ubuntu bascially following all the defaults and now it claims it's booting up ok (only error it reports is it cannot connect to the internet to set time, but since this computer isn't on line at the moment, that's fine).

But once it starts up I am asked for log in and password which is accepts and then I have a command line - what do I type to start the desktop - or do I have a problem since it does not start automatically?

In so far as I know there is no problem with any of the components of this computer - it's just a very underpowered machine for hardware hungry MS applications.

---

### Post by Protex on 2006-02-17
Type: 'startx'

That should do it, otherwise there may be a driver issue.

---

### Post by Eloise on 2006-02-17
thanks, Mitch - I try it when I get home this evening. Odd - I could not find any indication anywhere that you need to do that and since I'm new to linux, I was baffled - tried "start," "go," "run," etc. :)

---

### Post by RiTarDid on 2008-01-22
thanks double =)
removed kdm from "services"....kubuntu-desktop pkg was just to try out, thought it was unecessary for xubuntu; boy was i wrong...would only boot to shell.  startx was a lifesaver!

---


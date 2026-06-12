---
title: "remote &quot;help me&quot; app [through Dyn IP + firewall] ?"
date: 2009-04-10
forum: Desktop Environments
---

### Post by iaw4 on 2009-04-10
I want to create a bootable ubuntu environment which can help my tech-challenged grandmother, who sits behind a firewall on a dynamic DNS allocated by her ISP.

most of this is easy.  here is the wrinkle:

every once in a while, someone screws up her system.  this is a depressingly regular occurrence.  so I want to have a bootable USB stick that I can give her, that she can boot and which allows me to fix her system.

the usb stick should have an application on it which she can click (or that is automatically invoked at startup) which registers her computer with my own ubuntu computer [static IP address] (so that I know her dynamic IP address, too) and which allows me to take control over her computer.  Thus, I need to punch through the firewall, too.  Obviously, this should be limited to her registering with 3 or 4 of my computers (all ubuntu); and the remote control over her machine should only be working from my 3 or 4 different machines.

it would probably be simpler if her app were to send an "invite" to my own machine, which I could simply accept; and which would then function like rdesktop or vnc.

I am not a helpdesk and don't want/need extensive other tools.  granma is not sophisticated, so asking her to do things on the command line or following complex instructions are out of the question.

Is there a simple solution?

sincerely,

/iaw

---

### Post by rozbarwinek on 2009-04-11
I have a better, simpler and safer solution for you :)
Install hamachi (as server) + NX Free :P
Tell me if you need instruction.

---


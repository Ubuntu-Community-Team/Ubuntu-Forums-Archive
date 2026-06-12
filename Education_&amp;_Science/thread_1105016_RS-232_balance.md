---
title: "RS-232 balance"
date: 2009-03-24
forum: Education &amp; Science
---

### Post by NikoC on 2009-03-24
Hi everyone,

I've been trying to find some guidelines on how to log data from an RS-232 port in Ubuntu, yet I've been unsuccessful so far! Here's the problem:

At work we have an analytical balance that can interface with an RS-232 port. Basically when you have to weigh a lot of samples it just sends the weights via the RS-232 port to a windows computer where the data are stored as a txt file that can easily be imported into openoffice. 

I was wondering if there is an application available that can do the same on an ubuntu (Jaunty Jackalope) machine without having to use wine or any form of virtualization software...

Thanks

---

### Post by hubie on 2009-03-25
I think all you need to do is use minicom.  [Here is an example]("http://csciwww.etsu.edu/tarnoff/labs4956/sermouse/sermouse.html") of how to capture mouse characters, which should be functionally equivalent to what you want to do.

---

### Post by Odemia on 2009-03-25
Does the balance just output and the PC just listen or is there any kind of program running on the PC that is listening and sending?

If the PC just needs to listen and log the data:
In the terminal "cat /dev/ttyS0 >> /path/logfile.txt".
You could even put that in a little script and have a launcher in the menu bar for it, make it as simple as possible for everyone else in the office.

Note if there is something on the PC that is listening and needs to respond to the balance the snippet above won't work.

---

### Post by NikoC on 2009-03-25
As far as I know, the PC is just listening... so thanks for the quick replies and I'll give those a try!

Cheers,

Niko

---

### Post by ahmatti on 2009-03-25
Hi,
I was faced with a similar problem a while back. After I solved it I put together a small guide, that may help you:
[http://www.mm.helsinki.fi/~mpastell/serial.pdf](http://www.mm.helsinki.fi/~mpastell/serial.pdf) 

Also, there is a program called ttylog that can be used from the command line. Its basically does the same thing as cat, but you can specify the baud rate.

---

### Post by NikoC on 2009-03-25
I'll take a look at that pdf you 've posted, thank ahmatti!

---

### Post by botaro on 2010-06-29
> **NikoC said:**
> I'll take a look at that pdf you 've posted, thank ahmatti!
Hi NicoC!

Did you solve your problem with your RS232 balance? I've been facing the same problem and I couldn't get through with those tips.
I'd appreciate if you could help me.
Tx in adv
Botaro

---

### Post by NikoC on 2010-06-30
Sorry to disappoint you on this one botaro, but I didn't manage to connect my ubuntu pc to the analytical balance... after giving it a couple of tries I finally gave up :(

I just took an old windows xp laptop that we still had lying around in the lab and hooked it up!

---


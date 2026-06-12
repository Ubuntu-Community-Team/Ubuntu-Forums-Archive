---
title: "Anyone know anything about this? (Glucose)"
date: 2006-08-17
forum: Desktop Environments
---

### Post by bazz on 2006-08-17
[http://lists.freedesktop.org/archives/xorg/2006-August/017527.html](http://lists.freedesktop.org/archives/xorg/2006-August/017527.html)

Ave,

just introducing simple sugar in the form of a new acceleration architecture.

In the spirit of being short and sweet, that fits very well with the concepts 
of Glucose:
- it's an OpenGL based acceleration architecture, 
- all driver code is limited to just initialising it (a call to 
glucoseDriverInit), which really could be eliminated as well, by cleverly 
hooking it up in the server... we might want to do that soon.
- it uses XGL code, so it accelerates everything using exactly the same paths 
as XGL does. So there's no duplicate code/work here. 

A short FAQ:

Q: It is what?
A: Acceleration architecture. Nothing more, nothing less.

Q: How do i get it?
A: Do "git checkout glucose" in your xserver git tree. 

Q: Does it work?
A: Not without the glucoseDriverInit hook right now. Otherwise with the right 
positioning of stars, some prayer and a whole lot of luck good things might 
happen.

Q: Why not XGL?
A: We already have a server. One that works rather well. With AIGLX all this 
server is lacking is a nice way of accelerating common rendering primitives. 
Glucose is that bridge. Between AIGLX and Glucose we have the complete 
solution. Furthermore my plan is to provide a smooth transition for apps that 
would like to mix Xrender with GL, with Glucose it's a rather simple thing to 
do.

Q: How many more acceleration architectures does X need?
A: My favourite number is 13 but I'm pretty busy so I'm going for 3. This one 
looks like the one to rule them all. 

Q: What's the status?
A: I'll try to add TODO tomorrow or day after and send it here as well. 
There's a few things that I'm not terribly happy about. The driver hook is 
pretty obvious. 
Other things that do matter quite a bit but require more work include fun with 
direct clients which will most likely turn into drm context switching with 
preemption and a full blown gpu scheduler which is something that'd be nice 
to have either way. The fact that greedy gl clients can pretty successfully 
monopolise the gpu is quite a problem if everything is layered on gl. So 
yeah, there's quite a bit of work ahead but at least we all can work on dri 
and improvements there will, basically, improve the whole desktop (besides 
email clients which are hopeless). 

Q: Where do babies come from?
A: Montana. 

Zack

---

### Post by murataht on 2006-08-17
i just read it last night. i found a link to it from slashdot i think. 
still i don't clearly understand what improvements it can bring to X. :confused:

---

### Post by Terracotta on 2006-10-02
> **murataht said:**
> i just read it last night. i found a link to it from slashdot i think. 
still i don't clearly understand what improvements it can bring to X. :confused:

It basically replaces XGL without the overhead of having two x-servers running (since XGL is an X-server that runs on top of another X-server).
It uses the code of XGL (so no duplication of effort, just using things learned from another implementation of the same goal), but it's implemented into the 'old' X-server. So you have all advantages of both AIGLX and XGL at the same time.

---


---
title: "Open Source Modbus"
date: 2007-04-30
forum: Education &amp; Science
---

### Post by rivera151 on 2007-04-30
I was wondering if any scientists/engineers would be interested in starting an open source MODBUS implementation.  I'm trying to start something using Mono, since this would enhance portability and productivity, but I'm open to other suggestions.  Also, I've never participated in open source projects, so tips in that area are definitely welcome.

I'm thinking of starting with a modbus server daemon, so that client applications can query this server.  This would also help in developing client applications greatly.  Please help this effort!

---

### Post by dsl on 2007-05-02
> **rivera151 said:**
> I was wondering if any scientists/engineers would be interested in starting an open source MODBUS implementation.  I'm trying to start something using Mono, since this would enhance portability and productivity, but I'm open to other suggestions.  Also, I've never participated in open source projects, so tips in that area are definitely welcome.

I'm thinking of starting with a modbus server daemon, so that client applications can query this server.  This would also help in developing client applications greatly.  Please help this effort!

Some years ago a customer asked me to interface via MODBUS a device (a small box with four or five keys and a 5 lines LCD display) to a PC. I wrote a C++ application under Damn Small Linux. I should still have it in some meander of my hard disk.

I remember that the application was layered, there was a low level dealing with MODBUS (commands, replies, CRCs, serial line) and a high level dealing with commands specific to the box.

Provided we are speaking of the same thing (I am surprised there could be any interest in MODBUS today), what I could do is ask my customer to allow me to put the low layer in the open source, then send you the files (as they are), so that you could use them as a starting point or do anything you like with them. What I cannot do, sorry, is participate in future development (except maybe answering short questions about the code I would send).

Let me know if I should do so.

Daniele

---

### Post by rivera151 on 2007-05-02
Cool.  I thought this post was gonna die.  I found someone interested at SourceForge; we have started to communicate.  [Here]("http://sourceforge.net/projects/serial-modbus/") is the project site.  You can send me stuff though, any help is appreciated.

---

### Post by dsl on 2007-05-22
Dear rivera151,

sorry for the long delay, it took me a long time to contact my customer. He gave his permission, at least for the part of the code relevant to modbus and not to the device, but this should be no problem.
I attach here a tgz containing six cpp files; please consider them under gpl/lgpl as you like, even if I hadn't the time to add the headers telling so.
Feel free to ask if necessary; I will reply according to my memory and my time.
Hope this can be of some use, if not throw them down the drain.

Daniele

---

### Post by greenday on 2007-06-07
Thank you so much for the modbus source, it will help me too.

---

### Post by kiao on 2007-12-12
Hello, everybody, I'm completly new to this forum but not new to the open source world.

I'm very interested as well to know if there are any possibilities to share the knowledge of the MODBUS. I'm an Process control engineer, familiar to modbus, but I'm looking for gateway based on modbus.

Tanks a lot for yours answers

---


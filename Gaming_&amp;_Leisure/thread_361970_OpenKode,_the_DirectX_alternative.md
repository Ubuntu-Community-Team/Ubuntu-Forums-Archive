---
title: "OpenKode, the DirectX alternative?"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by magicsmoke on 2007-02-15
LinuxDevices.com showed this article back in December:

[http://www.linuxdevices.com/news/NS2485072825.html](http://www.linuxdevices.com/news/NS2485072825.html)

saying that OpenKode by the Khronos group could be a DirectX alternative.  A press release by the group came out a couple days ago explaining it:

[http://www.khronos.org/news/press/releases/rel41.html](http://www.khronos.org/news/press/releases/rel41.html)

and their overview of it:

[http://www.khronos.org/openkode/](http://www.khronos.org/openkode/)

From my reading, it's geared towards mobile devices, but couldn't it be done for the desktop as well?  I guess I'm wondering if this is the break Linux gaming has been looking for, or at least a step in that direction.  Let me know what you think.

---

### Post by Breepee on 2007-02-15
Well, it's the kind of thing Linux needs if gaming is ever to take off. OpenKode seems to be targetted towards integrated devices though, cellphones and the likes.

There's an DX alternative for personal computers, [SDL]("http://www.libsdl.org/"). It's still leagues behind DX, and development appears to be going very slow, but it's the best thing we have. OpenKode doesn't seem to add much functionality compared to SDL, so I think it's main target indeed is embedded devices.

---

### Post by TechZilla on 2013-02-09
I truly apologize for resurrecting this half-decade thread, but the information presented must be corrected.

The DirectX alternative, in this context, is the entire Kronos API collection.  OpenKODE is just one component, out of the many, which make up the collection.  

Regarding OpenKODE, it's primary goal is OS functionality abstraction.
Specifically one would use the OpenKODE API, instead of the more platform specific POSIX API.  I've attached the architectural graph, which is also available at the Kronos OpenKODE webpage.  It clearly display's where the components fit, in context to the greater system.

On another subject, if you're starting a project, and it would benefit from a DirectX alternative.  I would suggest SDL, as it's so mature and well established.  Although hopefully the Kronos API's will see greater adoption, as they're excellent API's.

---


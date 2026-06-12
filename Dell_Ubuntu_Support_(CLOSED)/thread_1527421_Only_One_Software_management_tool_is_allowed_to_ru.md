---
title: "Only One Software management tool is allowed to run at the same time"
date: 2010-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by edwino122 on 2010-07-09
I am a beginner in ubuntu and need some help on this error: ' Only one software management tool is allowed to run at the same time'. I am trying to instal avast.deb on my dell inspiron laptop. Any help would be appreciated. Thanks

---

### Post by tenhi on 2010-07-09
i suppose you have Ubuntu Software Center running and at the same time installing .deb package or whatever.

try to run 
*ps ax | grep apt *

and check apt instances running.

---

### Post by MCVenom on 2010-07-09
The software management tools (the programs that use apt as a backend) in Ubuntu are the Ubuntu Software Center, Synaptic Package Manager, Update Manager and I think Computer Janitor and Hardware Drivers (if you're downloading a driver) also.

If you try to use two or more of these apps at the same time, you'll get an error; this is probably the cause of your problem.

---


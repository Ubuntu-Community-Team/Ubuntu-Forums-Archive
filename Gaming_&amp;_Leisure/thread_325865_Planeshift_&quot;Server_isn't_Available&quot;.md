---
title: "Planeshift &quot;Server isn't Available&quot;"
date: 2006-12-26
forum: Gaming &amp; Leisure
---

### Post by smartbei on 2006-12-26
I just installed PlaneShift and updated it. When running the client I the server is unavailable. In the little "Servers" selection list, where there is only one server - Fragnetics - in the bar that says Fragnetics a percentage goes down...and then says Failed... after a couple seconds it tries again. Pressing okay gives me a "The server isn't available!" error.

I suspect that my router is blocking the port Planeshift is using. What port is this/How can I find out what port this is? 

Thanks!

---

### Post by smartbei on 2006-12-27
Solved with:
```
sudo tcpdump
```
and starting the program. Apparently, PlaneShift uses port 7777, which was indeed blocked.

---


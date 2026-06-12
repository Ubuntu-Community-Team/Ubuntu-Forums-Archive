---
title: "Jose chess doesn't want to play me"
date: 2008-08-27
forum: Gaming &amp; Leisure
---

### Post by guaso on 2008-08-27
New Ubuntu user here. I installed Jose chess, but as soon as I go out of book in a game I get an error message and Jose stops working. It happens with both crafty and toga II as soon as I deviate from the main line, even in move 1 if I attempt 1. h4 or something similar. What can I do to resolve this?

---

### Post by Crafty Kisses on 2008-08-28
What happens if you run it in Terminal, do you get any errors?

---

### Post by guaso on 2008-08-28
> **Codename said:**
> What happens if you run it in Terminal, do you get any errors?

Thanks for the answer codename. I tried running it with Alt-F2 and from the terminal with java -jar jose.jar. Every time it freezes as soon as I deviate from whatever book it is using. And it plays the Najdorf every time I play 1.e4. I attached a screenshot of the error message.

this is the content of the error log:

java.io.IOException: uciok expected
	at de.jose.plugin.UciPlugin.open(UciPlugin.java:248)
	at de.jose.Application.openEnginePlugin(Application.java:3527)
	at de.jose.Application$80.run(Application.java:3382)
 ---- Version Info ----
 jose: 1.4.4
 OS:   Linux 2.6.24-19-generic
 Arch:  i386
 Java: 1.6.0_06-b02
 ----------------------
 ---- Thu Aug 28 22:14:07 CDT 2008 ---- 
java.io.IOException: uciok expected
	at de.jose.plugin.UciPlugin.open(UciPlugin.java:248)
	at de.jose.Application.openEnginePlugin(Application.java:3527)
	at de.jose.Application$80.run(Application.java:3382)

---

### Post by Prisemut on 2008-08-29
I had the same problem and don't find a solution.
My workaround: I use the engine spike 1.2 Turin with OCI-Protocol, that works!

---

### Post by Crafty Kisses on 2008-08-29
From the looks of it, it looks like you're missing some Java plugins.

---


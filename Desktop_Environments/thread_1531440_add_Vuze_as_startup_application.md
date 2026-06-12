---
title: "add Vuze as startup application"
date: 2010-07-15
forum: Desktop Environments
---

### Post by kysato on 2010-07-15
This will be the first of many posts/questions I am sure, I have very little working knowledge of ubuntu or of linux period.

So far I have been able to figure out how to get Vuz installed properly and running, however I would like to make it start the gui interface automatically on login/startup and minimized. I tried adding it to the SYSTEM->PREFERENCES->STARTUP APPLICATIONS as that seemed the obvious way to do it, however it does not startup automatically after I restart the system.

I am running:
Ubuntu 10.04 LTS
Java 1.6.0_18
 Sun Microsystems Inc.
SWT v3555, gtk
Linux v2.6.32-23-generic, i386
Vuze V4.3.0.6/4 az3

thank you for any assistance.

---

### Post by HenneBaby02 on 2010-07-15
I haven't gotten around to re installing vuze yet, but did you check preferences for a boot on startup option ?

---

### Post by kysato on 2010-07-15
yes, I still run vuze on my old xp box which has that option. the Startup & Shutdown section is missing from the linux release of vuze :(

---

### Post by kysato on 2010-07-16
I started from scratch and it now seems that simply adding the command  'azureus' in teh startup applications will make it start, although it does not start minimized. I  also made a post on the vuze forums hoping someone there might be able  to help me as well.

so I am one step closer, just need to figure out how to make it minimized on run.

found the final part of my solution on the vuze forums... making me feel dumb again :\

Tools -> Options -> Interface -> Start: Start  minimized

it was actually an option in a different section, buried deeper than it is in the windows version

---


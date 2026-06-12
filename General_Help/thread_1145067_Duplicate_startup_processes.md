---
title: "Duplicate startup processes"
date: 2009-05-01
forum: General Help
---

### Post by pah99 on 2009-05-01
Hey I have a weird problem. When I boot my laptop, the processes start to load and they start in duplicates. If someone knows where I can access boot up logs, I could post what it is.

But basically its something like, 

fglrx-ati
fglrx-ati

pulseaudio
pulseaudio

etc. This isn't exact, but this is what it looks like. 

Any ideas on how to fix it?

---

### Post by zigga15 on 2009-05-01
system>preferences>session(or startup manager)

If its listed in their kill it. Otherwise I would say it is a problem in a lower conf file somewhere. check ~/.config/autostart

~ Dan

---

### Post by pah99 on 2009-05-01
No, there were no duplicates in Startup Applications. 
And ~.config/autostart also ended in no results.

The ati and pulseaudio are not the only two that do that. It duplicates all of the startup processes. I just gave that as an example. 

Just so you know, I have checked /etc/rc*.d and there are no duplicates in those either.

---

### Post by zigga15 on 2009-05-01
Not a direct solution, but should be some info in here:

[http://www.novell.com/coolsolutions/feature/15380.html](http://www.novell.com/coolsolutions/feature/15380.html)

unfortunately the start up stuff is all over the place (from the GUI to the back end, and from apps to superuser activated daemons)

Please let us all know how it went

---


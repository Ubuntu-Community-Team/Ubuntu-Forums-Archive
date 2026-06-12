---
title: "AWN calendar applet failure"
date: 2010-02-19
forum: Desktop Environments
---

### Post by Docaltmed on 2010-02-19
Using AWN 0.3.9 on Ubuntu 9.10. AWN calendar applet returns the message "Unable to return calendar data from external source" when started. It is configured to read Evolution which is functioning normally. Suggestions?

---

### Post by Docaltmed on 2010-04-10
Egad. I hate being the only one in the universe with a particular problem.

---

### Post by Groucho Marxist on 2010-06-07
> **Docaltmed said:**
> Using AWN 0.3.9 on Ubuntu 9.10. AWN calendar applet returns the message "Unable to return calendar data from external source" when started. It is configured to read Evolution which is functioning normally. Suggestions?

I'm having the exact same problem. Has anyone figured out how to fix this particular bug?

---

### Post by lmalek on 2010-08-11
I had the same problem. The list of AWN dependances can be found at his page [http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix]("http://wiki.awn-project.org/Awn_Extras:Dependency_Matrix").
To make Clock/Calendar Applet work it should be enough to install python-dateutil  
```
sudo aptitude install python-dateutil 
```
however if you want to integrate it with Google Calendar and Evolution you should also add
```
sudo aptitude install python-gdata python-vobject
```

---

### Post by ben2talk on 2011-02-03
That didn't fix it - it can't read Google Calendar and doesn't ask me for any account details to allow it to login/retrieve/integrate with the api in any way.

---


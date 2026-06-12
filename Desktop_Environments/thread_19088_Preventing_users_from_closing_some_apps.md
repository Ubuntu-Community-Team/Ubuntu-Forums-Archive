---
title: "Preventing users from closing some apps?"
date: 2005-03-10
forum: Desktop Environments
---

### Post by yanik on 2005-03-10
Hi everyone

In gnome, is there a way to prevent users from closing certain apps (that were auto started on login thru gnome-session)?  Like firefox and/or openoffice for example?  

Thanks

Yanik

---

### Post by valadil on 2005-03-10
Nope!  But you can make the apps come back to life after they've been killed.  Behold (use a terminal for this of course):

while true ; do glxgears ; done

Whenever you close the glxgears window a new one pops up.  Just run an app that isn't glxgears and you're all set.  You may have to play around with the session manager a bit since it can be bizarre at times, but I don't really know how to help with that part.  Maybe replacing the firefox command in gnome-session with the command above?

---

### Post by yanik on 2005-03-10
Well, the idea was to cut down on long loading times...

There certainly must be a way, I'll keep looking, thanks anyway valadil

Yanik

---

### Post by valadil on 2005-03-10
Ah.  You should have said so.  Openoffice (and maybe firefox, though I haven't checked) has applets (or daemons, I can't remember since I don't use them) that you leave running.  They load all of OO's libs into memory to drastically reduce its startup time.  Something like that may be more akin to what you're looking for.

---


---
title: "&quot;Firefox is running, but is not responding&quot;"
date: 2006-09-27
forum: Desktop Environments
---

### Post by James_Nostack on 2006-09-27
I get this error occasionally when I try to run Firefox.  It started soon after I installed Beagle, but this was shortly after upgrading to Ubuntu 6.06 so I'm not sure what's causing it.

The full error message:
"Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process, or restart your system."

It's trivial to fix-- I go to System, Administration, System Monitor, where I find... "Firefox-bin    Sleeping    29.1 MiB" and terminate the process, at which point things are fine. 

But still, it's annoying.  It doesn't happen all the time, just occasionally.  Is there any way to fix this problem?

---

### Post by croak77 on 2006-09-27
Did you add any extensions to firefox?

---

### Post by marianom on 2006-09-27
Find your answer @ the mozillazine kb:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by James_Nostack on 2006-09-27
I installed Beagle earlier, and this problem happened shortly afterward.  

So I went to Tools, Extensions, and removed the Beagle Extension.  So far, everything works fine.

---


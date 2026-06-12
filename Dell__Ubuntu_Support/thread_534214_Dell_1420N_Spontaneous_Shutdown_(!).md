---
title: "Dell 1420N Spontaneous Shutdown (!)"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by teich on 2007-08-24
Hi All,

My new Dell 1420N is having a spontaneous-shutoff problem.  

* Only happens between power-on and shortly after I log-in (within a few seconds).
* Fan is running at full drive when it happens.
* Never happens twice in a row, i.e. within a few minutes.

Because of said symptoms it's not really gotten in the way, but seems like a serious problem that should be dealt with.  Poking around in the BIOS hasn't revealed any relevant settings.

Has this happened to anyone else?

---

### Post by Paul S on 2007-08-25
No such problem.  But, be sure to check your keyboard shortcuts and make sure you don't have some key combo configured that causes you to turn it off.

Also, you may want to run the dell diagnostics when you get some time, just to be sure some hardware glitch does not exist.

regards,

---

### Post by jso2897 on 2007-08-25
One quick thing you might try is booting up the LiveCD, ans selecting "memory test" from the menu. If there is something goofy in the ram, this can be the result.

---

### Post by teich on 2007-08-26
Paul S -- I should be more specific.  Mostly the problem occurs when I am not even near the computer, as I turn it on and walk away while it boots.

jso -- Good point, I'll try the memory test tonight.

---

### Post by Paul S on 2007-08-26
One of the dell diagnostic tests is on memory.

Another thing to check is the /var/log/messages file (as well as dmesg, syslog, kern.log, etc. .. all in /var/log directory) to see what messages were captured just at the time of shutdown.  There may be a clue there.

regards,

---

### Post by jay4e on 2007-08-27
been running for over a month now and not see any problems with shutting down.  dose it do a normal shutdown or just a hard restart?

---


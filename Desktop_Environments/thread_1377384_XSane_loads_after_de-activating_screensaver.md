---
title: "XSane loads after de-activating screensaver"
date: 2010-01-10
forum: Desktop Environments
---

### Post by bods on 2010-01-10
Hello - hoping someone here might be able to give some advise.

I'm using GNOME under Ubuntu 9.10 - I've used Ubuntu for several years, and upgraded several times.

Just recently I've had a slightly odd problem.

The screensaver kicks in as normal (I have it set to blank screen).  Then when I return and deactivate it, XSane loads.  I've not been able to find anything out from Google - I presume there's some method of autoloading applications when a screensaver kicks in that's somehow turned itself on, however I can't find any reference to it.

Has anyone any ideas?  Other than the obvious "turn the screensaver off" ;)

thanks!

---

### Post by bods on 2010-01-28
If it helps, I've tracked this down to nothing to do with the screensaver but when I turn my monitor on or off?

Anyone any idea?  Please?

---

### Post by stars on 2010-01-28
if you dont need sane, you could shut down or disable it with sysv-rc-conf 
grab it using synaptic, then from a terminal type sudo sysv-rc-conf 
the service name is saned
arrow down to it, then use the minus key to turn it off
to make this permanent uncheck the runlevels using the spacebar

---

### Post by bods on 2010-01-28
Thanks for the idea I do need sane I'm afraid, but I now don't think it's a sane issue.  I turned on my printer for the first time just now and lo, when I turned it off, xsane launched!

Which gave me a clue.  My printer is connected by USB to the USB hub on my monitor.  So when I turn the monitor on, the printer USB cable is obviously located.  If I remove the printer cable and put it in again (even with the printer turned off), xsane launches.  So I presume its something to do with device detection.

---


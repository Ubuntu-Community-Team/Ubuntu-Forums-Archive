---
title: "System program problem detected"
date: 2013-01-20
forum: Desktop Environments
---

### Post by 1cookie on 2013-01-20
hi

I keep getting a system notice:  [http://acookson.org/wp-content/uploads/2013/01/system-error.png](http://acookson.org/wp-content/uploads/2013/01/system-error.png)

which keeps popping up after every restart. Has anyone had this problem, and how severe is it?

Ubuntu 12.10

---

### Post by sammiev on 2013-01-20
If you click on report problem you will see what was causing it.

---

### Post by sanderj on 2013-01-20
> **1cookie said:**
> hi

I keep getting a system notice:  [http://acookson.org/wp-content/uploads/2013/01/system-error.png](http://acookson.org/wp-content/uploads/2013/01/system-error.png)

which keeps popping up after every restart. Has anyone had this problem, and how severe is it?

Ubuntu 12.10

I have the exact same problem. My Ubuntu 12.10 is an upgrade Ubuntu 12.04, FWIW.

I just move the error popup message out of the screen.

---

### Post by 1cookie on 2013-01-20
> **sammiev said:**
> If you click on report problem you will see what was causing it.

OK. I do that, provide my root password and am then taken to:

[http://acookson.org/wp-content/uploads/2013/01/failure.png](http://acookson.org/wp-content/uploads/2013/01/failure.png)

which is not the most helpful unfortunately. I'm not overley worried, I can always reinstall the distro; but would like to avoid that if unecessary.    I suppose my main concern would lie with security.

---

### Post by sanderj on 2013-01-20
> **sammiev said:**
> If you click on report problem you will see what was causing it.

ExecutablePath: /usr/share/apport/apportcheckresum

Package: linux-image-3.5.0-21-generic 3.5.0-21.32

Annotation: "this occurred during a previous suspend and prevented it from resuming properly"

Failure: suspend/resume


This happens after a plain reboot, so AFAIK there is no resume involved.

I must say Ubuntu 12.10 sometimes has problems really rebooting this system: it then just goes back to the login screen, instead of rebooting like I request ("Restart" or "Shut Down" from the upper right corner).

---

### Post by sanderj on 2013-01-20
Update:

I closed all programs, opened a terminal, did a "sudo shutdown now", Ubuntu shut down, I removed the power cord and the battery, reconnected everything, restarted Ubuntu, and ... I did NOT get the suspend/resume error message.

Interesting ...

---

### Post by 1cookie on 2013-01-20
> **sanderj said:**
> Update:

I closed all programs, opened a terminal, did a "sudo shutdown now", Ubuntu shut down, I removed the power cord and the battery, reconnected everything, restarted Ubuntu, and ... I did NOT get the suspend/resume error message.

Interesting ...
I tried this. The system just hung with me having to forceibly unplug the cable to shutdown. Restart and the problem persists. :(

---

### Post by VanillaMozilla on 2013-01-22
> **sammiev said:**
> If you click on report problem you will see what was causing it.
I've had the same problem for months.  "Report problem" gives no result.  Suggestions?

---

### Post by sammiev on 2013-01-22
> **VanillaMozilla said:**
> I've had the same problem for months.  "Report problem" gives no result.  Suggestions?

Xorg is the problem but when I go to report the problem I get some message that the error info has changed since the 1st error. I seem to get this error 2 weeks after the main release of the last 2 releases. I use some other OS which is based off Ubuntu and I do not get the error any more.

---


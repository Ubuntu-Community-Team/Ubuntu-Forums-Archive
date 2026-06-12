---
title: "Strange nmap error"
date: 2009-04-17
forum: General Help
---

### Post by moonpup on 2009-04-17
When running nmap against localhost, it now returns this weird timing error and exits.

nmap: timing.cc:339: void RateMeter::update(u32, u32, const timeval*): Assertion `diff >= 0.0' failed.
Aborted

Running nmap on external hosts is working fine. Any idea on why this fails against localhost when it used to work?

---

### Post by brian_p on 2009-04-17
> **moonpup said:**
> 

Running nmap on external hosts is working fine. Any idea on why this fails against localhost when it used to work?

Your version of nmap might have been useful to know. Anyway, it looks like a bug:

[http://seclists.org/nmap-dev/2008/q2/0120.html](http://seclists.org/nmap-dev/2008/q2/0120.html)

---

### Post by moonpup on 2009-04-17
Thanks for the link. Interesting as that post shows the exact same error at the end. I'm using nmap from the repos and the version is:

ii  nmap  4.62-1ubuntu1 The Network Mapper

---

### Post by brian_p on 2009-04-17
> **moonpup said:**
> Thanks for the link. Interesting as that post shows the exact same error at the end. I'm using nmap from the repos and the version is:

ii  nmap  4.62-1ubuntu1 The Network Mapper

Excerpt from Nmap 4.68 [2008-6-28] changelog:

> Fixed a crash in RateMeter::update() which could lead to an error
  saying "diff >= 0.0" assertion failed.  I think the problem was
  actually caused by SMP machines which didn't sync the clock time
  perfectly.  This lead to gettimeofday() sometimes reporting that
  time decreased by some microseconds.  Now Nmap is willing to
  tolerate decreases of up to 1 millisecond in this function. [Fyodor]

---

### Post by moonpup on 2009-04-17
Thanks Brian! I can't find 4.68 in the repos... maybe I'll pull the current version from insecure.org myself.

---

### Post by brian_p on 2009-04-17
> **moonpup said:**
> Thanks Brian! I can't find 4.68 in the repos... maybe I'll pull the current version from insecure.org myself.

It's in jaunty. And Debian has it. But you'd have to look at the dependencies.

Or you could backport it to hardy. pbuilder, perhaps.

---

### Post by moonpup on 2009-04-17
I'm all set, I pulled 4.68 from debian unstable and installed it. It gives a timing warning but still works. Thanks for the follow up and help!

---


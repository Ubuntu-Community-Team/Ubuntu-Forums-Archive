---
title: "sound-juicer not starting/problem"
date: 2006-09-01
forum: Desktop Environments
---

### Post by dynacrylic on 2006-09-01
When I run sound-juicer the application never starts.

I've tried it from the applications >> sound n video menu and from the shell. I've also tried unistalling/installing and reinstalling completely. 

Any tips to just get the app started?

---

### Post by dynacrylic on 2006-09-01
Problem solved.

I started thinking that if 'maybe' i had a background process already running (such as another instance of s-j) it might not start up.  I did a "ps -ef" and killed of the 8 instances of s-j running.

once they were all killed i clicked on s-j and voila!

---


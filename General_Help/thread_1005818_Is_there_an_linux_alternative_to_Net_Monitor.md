---
title: "Is there an linux alternative to Net Monitor"
date: 2008-12-08
forum: General Help
---

### Post by yaknowwat on 2008-12-08
I'm curious about this because it seems to be a nicely done application.  It's key features are that it can monitor an entire network of computers easily like screen blocking (presents a message that refreshes itself to front every half second or something stopping people from playing with the remote computers) , process killing, shut downs, etc.  Along with allowing the admin kiosk to present their desktop to remote users without the remote users having to press a button I'm sure there is a process running to listen for the signal no avoiding that though.

I was wondering if linux has any applications that rival this.
( It is actually a very useful tool for schools and linux should have something to rival it or even surpass it in functionality and ease of use to the end user admin  -The admin is normally just a random teacher-. )
 [http://www.networklookout.com/employees_pro.htm](http://www.networklookout.com/employees_pro.htm)

---

### Post by jimv on 2008-12-08
I can't think of any particular software product that would do that, though you could achieve similar results with VNC and SSH.

SSH lets you transparently monitor processes and perform administration tasks, while VNC, when configured correctly, can allow you to watch what specific users are doing and/or take control.

I think there's not going to be a software package like what you're looking for because Linux workstations are still pretty uncommon.

It probably wouldn't be too hard to put together a web-app that would do those things.  (Note to self :)

---

### Post by yaknowwat on 2008-12-09
> **jimv said:**
> I can't think of any particular software product that would do that, though you could achieve similar results with VNC and SSH.

SSH lets you transparently monitor processes and perform administration tasks, while VNC, when configured correctly, can allow you to watch what specific users are doing and/or take control.

I think there's not going to be a software package like what you're looking for because Linux workstations are still pretty uncommon.

It probably wouldn't be too hard to put together a web-app that would do those things.  (Note to self :)

Thing is it needs to be centralized and a web app wouldn't cut it because it would need to be run transparently at well done speeds with administration rights (so a rouge user couldn't mess it up) probably through policy kit.  Though an extra web app i suppose would work for the remote presentation part as it could be used for people who come in with their own laptops.

Thing is if linux had an easy to use tool like this surpassing the proprietary ones linux workstations would definitely become more common, because a tool like this is a great assistant in not only administration , but teaching alike.

---

### Post by rudihawk on 2008-12-09
I think you should check out something called "vnstat". Its in the repos.

---

### Post by yaknowwat on 2008-12-09
> **rudihawk said:**
> I think you should check out something called "vnstat". Its in the repos.

Very far off from what I'm talking about.  Yes I know the application having the name Net Monitor is horribly misleading, but thats what the company oddly decided to name it.

---

### Post by howlingmadhowie on 2008-12-09
why bother? just log in to each computer over ssh in a screen session.

---

### Post by yaknowwat on 2008-12-09
> **howlingmadhowie said:**
> why bother? just log in to each computer over ssh in a screen session.

It needs to be something a teacher could use that barely under stands it you can't expect every teacher to have IT level knowledge  they just don't want to have all that info.

Logging into each computer would be time consuming yes i know you can go ahead and use a shell script but even with SSH and shell scripting the ease of use is still not there for managing the average of 30 computers or more.

also with SSH is it even possible to present your screen to all the computers your logged into at once without the user having to press a button only the admin (teacher).

---


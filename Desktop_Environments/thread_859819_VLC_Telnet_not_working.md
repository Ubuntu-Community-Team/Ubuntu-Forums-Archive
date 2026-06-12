---
title: "VLC Telnet not working"
date: 2008-07-14
forum: Desktop Environments
---

### Post by pepsifx357 on 2008-07-14
I've been using Ubuntu for about 5 months so go easy on me.

I was wanting to set up a multi cast on demand video server and I have failed pretty much utterly.  

I installed VLC and got a single stream to work numerous times.

I'm not exactly sure how to set it up.  I want it to continually run in the back ground and users be able to connect over the interet/network and use it without it having to run in the fore ground.

Is this possible?  Kinda like Squeeze Center?

And if so, how can I set up the http interface so I can use it like so.

Thank you for any posts you leave,
Ben

---

### Post by pepsifx357 on 2008-07-18
anyone?

---

### Post by pepsifx357 on 2008-07-18
My system is behind a NAT router kinda like the internet you find at dorm houses. And every port is blocked.  Would that have an effect on my local intranet which is behind a wireless router?

---

### Post by gcbzzzz on 2008-12-28
no. one network can't affect others.

vlc --extraintf http  --extraintf telnet

now, keep in mind that both of those interfaces are mostly useless and have arcane ways to be used.

they don't seem to be built for regular users and lack the proper documentation.

good luck

---


---
title: "Email notification needed when ac adapter is offline"
date: 2009-02-22
forum: Desktop Environments
---

### Post by headlice on 2009-02-22
Hi,

What program would I use to send an email from a laptop Ubuntu 8.10 machine if the ac adapter goes offline?

I am using a laptop with the desktop environment as a server and the ac adapter has a bad connection by the brick in the powercord.  If it gets bumped or something, it has a tendency to stop drawing power from the outlet, then the laptop battery kicks in and the pc dies in an hour or so.

I would like it to send me an email so I can fix it before it dies.

Thanks.

---

### Post by komputes on 2009-02-24
You would need to hack together a script that runs when the the battery is at 10% and email you via telnet, which is scriptable. I'm not too familiar with what is already available here in terms of applications.

You may want to also look into a service called Landscape which is run by Canonical. It will alert you by email independently of your computer. It can contact you if you machine goes offline or needs to be updated. You can control your computer from the website.

Check it out

[http://landscape.canonical.com](http://landscape.canonical.com)

---

### Post by teppa on 2011-01-31
headlice, did you solve the problem?

i would like to know how.


thanks!

---


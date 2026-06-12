---
title: "Admin privileges to connect to ISP via modem?"
date: 2006-02-26
forum: Desktop Environments
---

### Post by optimaco on 2006-02-26
Hi,
I just installed Ubuntu 5.10 and created a new user with 'Desktop' profile. This profile includes the privileges 'Use modem' and 'Connect to the internet using a modem'. 
However, when I log in as this user and try to activate the modem (via the Gnome Modem Monitor panel applet), I get a message 'To connect to your ISP, you need administrator privileges' :( . The dialog requires a password, and of course the user password fails. 
Why is it that the user needs admin privileges for something as simple as browsing the web? Can I change that?

---

### Post by optimaco on 2006-02-26
Well, well. I finallly got this thing working, but NOT using the Gnome Modem Monitor applet (MUST have admin privileges).
I installed Gnome-ppp, which does the job.
I also tested pppconfig and pon / poff (works fine as well) but I find it not very user friendly for users that are not 'computer litterate'. Although a small script placed on the Desktop that they can simply click helps them (Connect / Disconnect modem).

---


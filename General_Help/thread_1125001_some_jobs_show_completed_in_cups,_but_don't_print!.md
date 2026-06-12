---
title: "some jobs show completed in cups, but don't print!"
date: 2009-04-13
forum: General Help
---

### Post by mp035 on 2009-04-13
Hi all, I have several machines on a network, but only 2 are of consequence for this problem:

1) linuxbox.local - this machine runs a cups print server and is usually used by me (user mark)

2) david-desktop.local - this machine is set to use linuxbox as its default print server via an /etc/cups/client.conf entry.  this machine is usually used by my brother (user david)

all was working until we started work on monday, now this is the scenario:

david@david-desktop can print to linuxbox from any program, except open office.
mark@david-desktop can print to linuxbox from any program
mark@linuxbox can print from any program (to localhost:631 server)
and just for reference, another user:
bianca@linuxlaptop can print to linuxbox from any program.

Does anyone know what I should check (in open office?) 

The david@david-desktop jobs show up in the cups queue on the linuxbox, with the status completed, but nothing comes out of the printer, not even a blank page!

Any hints or suggestions would be most welcome, thanks.

---

### Post by mp035 on 2009-04-14
bump... anyone?

---

### Post by khelben1979 on 2009-04-14
What version of Ubuntu including Open Office are you running over there?

---

### Post by mp035 on 2009-04-14
Thanks for the reply.  I am using Hardy Heron with OOo 2.4

---

### Post by mp035 on 2009-04-15
bump... 

anyone, still got the same problem, I've tried deleting david's ~/.openoffice.org and ~/.openoffice.org2 directories, but still no change in behavior.

Anyone?? :)

---

### Post by khelben1979 on 2009-04-16
If there really is a problem with your Open Office and not your system, then these 2 forums is great for searching for information:

[OpenOffice.org Community Forum]("http://user.services.openoffice.org/en/forum/index.php") and [the OpenOffice.org Forum]("http://www.oooforum.org/").

---

### Post by mp035 on 2009-04-16
thanks for the links.  will try in the next 24 and post any results.  (time zones make the replies at awkward hours), but many thanks for all interest. pls keep an eye on this, as I had a similar problem with OOo 3 but downgrading to 2.4 fixed it.

thanks again, will post in 24.

---


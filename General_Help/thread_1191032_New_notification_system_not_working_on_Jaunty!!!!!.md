---
title: "New notification system not working on Jaunty!!!!!!! Help!!"
date: 2009-06-18
forum: General Help
---

### Post by Arquis on 2009-06-18
[SIZE=3]Hi,

I am using Jaunty and for some strange reason the new notification system stopped working. Instead Jaunty is using the old one from Intrepid and I can't make it revert to the new notifier. I tried reinstalling notify-osd and the notification-daemon (is this right or is this the old one?) to no avail.

Please help. Google results turned nothing and I am going crazy over this little thing.[/SIZE] :o


Any suggestions are welcome. Thank you.

---

### Post by MyR on 2009-06-18
welcome to the forum!

is notify-osd running?

peace

---

### Post by Arquis on 2009-06-18
Hi Myr. Thanks for the reply.

Notify-osd is not on the System Monitor neither in the Services list. I tried to run it on the command line (i found it but searching the file) but nothing happened. Is this the problem? It should appear on the System Monitor?

---

### Post by Arquis on 2009-06-18
I should add that there is no NOTIFY-OSD set on auto-start in the Sessions window. Strange... 

Thanks again.

---

### Post by MyR on 2009-06-18
notify-osd would appear in the system monitor if it were running.  I don't have anything called notify-osd in my startup applications either.

If you have it installed correctly you just have to figure out how to start it.  Sorry but I don't know how because I have not experienced this problem. You could try [this website.]("http://blog.alexrybicki.com/2009/02/how-to-install-notify-osd-in-intrepid.html")
good luck!

peace

---

### Post by Arquis on 2009-06-18
Thanks. That site is for Ubuntu 8.04 and is not the answer, but you gave me another idea and I solved the problem.

Seems to be a bug with AWN Notification Applet. When it is on, Notify-OSD goes nuts. Just turn the AWN Notification Applet off and everything is back to normal. Incredible to say the least. So easy to fix but so hard to discover the problem!!

I thank you for trying to help anyway. Ubuntu has a great community indeed. :)

---


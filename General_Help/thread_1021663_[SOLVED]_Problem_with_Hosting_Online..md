---
title: "[SOLVED] Problem with Hosting Online."
date: 2008-12-25
forum: General Help
---

### Post by XFaisalX on 2008-12-25
Hey guys.
I have a little problem.
I tried to host a teamspeak and source dedicated server server, but other people can't connect.
I have set my static IP already, and tried various tutorials, without result.
Could anyone help out please? =/
(P.S. I use Ubuntu Server Edition 8.10)
Maybe I need an app installed?

---

### Post by Ahadiel on 2008-12-25
Have you forwarded the corresponding ports to your server?

[http://portforward.com/](http://portforward.com/)

---

### Post by XFaisalX on 2008-12-25
I don't use a router on my Linux Server Edition computer. =P

---

### Post by albinootje on 2008-12-25
> **XFaisalX said:**
> I don't use a router on my Linux Server Edition computer. =P

How is your server connected to the Internet ?
If you don't have a DSL-router or cable-modem, is it hosted in a data-centre of a webhosting company then ?

---

### Post by XFaisalX on 2008-12-25
Sorry for late response.
It's directly connected to the modem.
I use Tele2 in case that's important.

---

### Post by albinootje on 2008-12-25
> **XFaisalX said:**
> Sorry for late response.
It's directly connected to the modem.
I use Tele2 in case that's important.

Okay.
For a cable-modem you would need to set up portforwarding in this scenario, or you need to find out how to make your cable-modem "transparent" so that all the ports of your Linux server become directly visible to the outside.
You can probably find out more in the manual of the cable-modem, or at the support pages of your ISP.
The earlier mentioned url posted by Ahadiel could also help you with that.

---

### Post by XFaisalX on 2008-12-25
Thank you very much, I was working on these servers for like 5 days, and almost more than 5 hours each day.
Finally I can put it up =D
Thanks for the help, I didn't know that modems needed their ports forwarded too, I never heard that one.
Thank you soooo much ^^

---

### Post by albinootje on 2008-12-25
> **XFaisalX said:**
> Thank you very much, I was working on these servers for like 5 days, and almost more than 5 hours each day.
Finally I can put it up =D
Thanks for the help, I didn't know that modems needed their ports forwarded too, I never heard that one.
Thank you soooo much ^^

You're welcome! Glad to see you can continue now.

---


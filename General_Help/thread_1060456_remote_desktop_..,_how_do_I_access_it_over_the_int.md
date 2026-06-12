---
title: "remote desktop .., how do I access it over the internet?"
date: 2009-02-04
forum: General Help
---

### Post by hurtstotalktoyou on 2009-02-04
Hi, all.

My remote desktop works great on my local network, but I'd like to set it up so that I can access it from another location, over the internet.  Does anyone know how to do that?

Thanks!

---

### Post by mykrob on 2009-02-04
provided you have a static WAN IP address, and also have set a static internal IP for the machine you want to control, you need to forward port 5900 on your router to the internal machine address. On my router, I also had to turn on UPnP.

Then, using the remote desktop connection app, point it to:

##.##.##.##:5900

replace the ##'s with your WAN IP address. Make sure to set the remote computer to accept incoming connections without needed user confirmation, but DO set a password to gain access.

Hope this helps.

---


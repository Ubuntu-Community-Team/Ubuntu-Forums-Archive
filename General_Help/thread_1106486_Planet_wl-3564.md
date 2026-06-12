---
title: "Planet wl-3564"
date: 2009-03-25
forum: General Help
---

### Post by petulko52 on 2009-03-25
Hey guys,

I just downloaded and intalled the UBUNTU and i really like it. I'm trying to get the internet working but becasue i'm so new in all this I have no idea where to start. I would like to use the UBUNTU OS to learn some more about it but i need to get connected. i have a PCMCIA CARD for my WIFI. It's PLANET WL-3564. It should be LINUX compatible but i don't know how to istall it. Here is the link of the product (it's in POLISH): [http://www.planet.pl/produkty/karty_sieciowe/wg_interfejsu/pcmcia/bezprzewodowe/wl_3564](http://www.planet.pl/produkty/karty_sieciowe/wg_interfejsu/pcmcia/bezprzewodowe/wl_3564) and here is the direc link for the download of the driver: [http://www.planet.pl/content/download/1392/7538/file/UT-WL3564v10b14.zip](http://www.planet.pl/content/download/1392/7538/file/UT-WL3564v10b14.zip)
I'm pretty good with WINDOWS OS but i'm so lost in this. Can I use this files to install the WIFI CARD on my computer in the UBUNTU environment? Thank you for answer and have a nice day.

Peter

---

### Post by mb_webguy on 2009-03-25
If it's supported by Linux, you don't have to install any drivers.  

If it's not supported by Linux, then you'll have to find the actual Windows driver (an .inf file) for the card and use ndisgtk.  The driver in that link unfortunately doesn't contain a separate inf file, and I haven't been able to locate it on the web anywhere.

---


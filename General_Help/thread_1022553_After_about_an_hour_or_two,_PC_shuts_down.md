---
title: "After about an hour or two, PC shuts down"
date: 2008-12-26
forum: General Help
---

### Post by n00b_saibot on 2008-12-26
Ubuntu 8.10

It usually happens while I'm watching a flash video on youtube or any another website.  When I turn the PC back on again.  It shuts down within seconds.  It keeps doing this until I give up and try the next morning in which case another hour or two and the whole problem starts again.

There is also a weird vertical green line that appears every so often.

Thank you.

---

### Post by Miljet on 2008-12-26
My first guess is that your system is shutting down due to overheating. I have noticed that my CPU temps really spike up after a short time of watching flash video on utube.

---

### Post by sdennie on 2008-12-27
This does sound like a classic example of overheating.  Flash will generally push your CPU usage close to 100% (for a core) and so it makes overheating more likely.  Try installing the sensors applet and adding it to the gnome panel to keep an eye on your CPU temperature:

```

sudo apt-get install sensors-applet

```

---

### Post by Hydrid on 2008-12-27
yes i agree with vor it seems temprature problem.See if all of your cooling systems are in place ;)

---


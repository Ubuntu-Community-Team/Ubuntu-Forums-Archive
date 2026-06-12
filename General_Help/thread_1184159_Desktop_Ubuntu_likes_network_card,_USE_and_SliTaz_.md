---
title: "Desktop Ubuntu likes network card, USE and SliTaz don't"
date: 2009-06-10
forum: General Help
---

### Post by fiddler616 on 2009-06-10
Hello,

I'm in the process of making a dinosaur laptop (~300 mHz) usable. It's borrowing 512 MB or RAM from a different machine, which let me install Jaunty...which was too slow. 

CrunchBang was more sluggish than Jaunty (what the heck?), so then I tried Jaunty Server, since I'll primarily be using it for programming, and a CLI is great for that. 

USE wouldn't recognize my PCMCIA wireless card. Which I accept, since Jaunty and CrunchBang had to install the Broadcom restricted driver. But they did recognize a PCMCIA wired network card, which USE doesn't. After that failure, I remembered hearing about SliTaz, and the website looked very appealing, so I burned a CD and booted off it. The speed is great, but it also doesn't recognize either card.

How do I fix this?

I can give you model numbers if you want them.

Thank you.

---

### Post by snowpine on 2009-06-12
I got my Broadcom wireless card working in Slitaz by downloading the windows driver and using ndiswrapper. You can also check over on the Slitaz forum; there are a couple of threads on the topic. Slitaz does not ship with proprietary drivers like ubuntu does.

---


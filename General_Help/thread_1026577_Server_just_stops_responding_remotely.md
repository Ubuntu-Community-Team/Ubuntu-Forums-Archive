---
title: "Server just stops responding remotely"
date: 2008-12-31
forum: General Help
---

### Post by bigman1052 on 2008-12-31
Ok so, I setup ubuntu server yesterday, setup apache2, mysql, postgresql, webmin, etc.  I forwarded the ports yesterday (22 for ssh, 80 for http, and 10000 for webmin).  So I leave my house this morning connected to the server internally form another computer.  I get to work and I can't SSH or use the web server.  So I run home, and low and behold I can connect internally.  So I remote into my work laptop and try to SSH again to see if I can get in and...nothing.  Restart the system and I'm good to go again?  Any thoughts?

---

### Post by taurus on 2008-12-31
Is your computer at home connected through a router?  Did you remember to open a port, 22, for incoming signal on your router?

---

### Post by bigman1052 on 2008-12-31
Yes, I reset the server itself and it worked. Didn't touch the router. The ports were already forwarded, just stop responding.  I'm going to upgrade the firmware on my router (wrt54g).  But other than that, I cant understand why it would do such a thing.

---


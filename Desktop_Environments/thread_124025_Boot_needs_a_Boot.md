---
title: "Boot needs a Boot"
date: 2006-01-31
forum: Desktop Environments
---

### Post by icarius on 2006-01-31
When booting up, Ubuntu takes about 5 minutes to configure the network devices,  how can I speed this up and not have to configure the network device manually?

---

### Post by matthew on 2006-01-31
The reason it is going slow is that Ubuntu is waiting for a response from the DHCP server. Either the server is slow, which is beyond your control, or there is a problem somewhere. What you could do is configure Ubuntu to use a static IP address rather than doing everything fresh with DHCP each time you boot. Whether you want to learn how to do that is up to you...it's not hard, but you will need to do a bit of research if you don't already know how. Or, you can just hit <crtl>+c each time, skip that step in the booting process and configure manually...but I gather you don't really want to do that. :)

---


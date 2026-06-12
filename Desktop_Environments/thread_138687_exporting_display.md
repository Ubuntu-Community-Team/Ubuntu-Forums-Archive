---
title: "exporting display"
date: 2006-03-02
forum: Desktop Environments
---

### Post by bryan139 on 2006-03-02
I have breezy installed under vmware here at school, networking and everything works fine. I can ssh to my home server, also running ubuntu, and from that to my home desktop, running ubuntu. How can I export the display of my desktop through my server to my school install of ubuntu?
Thanks,
-bryan

---

### Post by hw-tph on 2006-03-02
On your home server, make sure /etc/ssh/sshd_config has X11Forwarding set to yes, and then - from school - simply type **ssh -X user@homeserver** (-X enables X11 forwarding). When logged in, simply start the program you want. You could run any program you want and have it displayed at your school computer. Apply an ampersand to detach from the console so you can continue typing commands (i.e. **firefox &**).


Håkan

---


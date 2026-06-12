---
title: "system-services doesn't list all system services"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Valhalla on 2005-12-11
So, I fired up the admin services program, and discovered that I there are only 10 things listed.  I'm assuming this is incorrect, since there are somewhere around 45 things in my /etc/init.d/ directory, and things like hplip, and hdparm are not listed.  Is this normal, and how can I make things like hdparm and 3rd party things like servers  start at boot?

---

### Post by dcstar on 2005-12-12
[QUOTE=Valhalla]So, I fired up the admin services program, and discovered that I there are only 10 things listed.  I'm assuming this is incorrect, since there are somewhere around 45 things in my /etc/init.d/ directory, and things like hplip, and hdparm are not listed.  Is this normal, and how can I make things like hdparm and 3rd party things like servers  start at boot?[/QUOTE]
Some things just run, make changes to config settings and exit, so there won't be any apparent "service".

If you want to see what is starting up, enable bootlogging in /etc/default/bootlogd.

---


---
title: "Apache 2.2.16 Vhosts Permissions Problem"
date: 2010-08-19
forum: Desktop Environments
---

### Post by Narkboy on 2010-08-19
Hi - brand new linux user, brand new forum member and stumped!

I've got Ubuntu 10.04 up and running on my laptop, and have begun to setup a lamp server. Everything is working fine except vhosts under apache. I'm running Apache 2.2.16 taken directly from apache.com as I tried the Ubuntu verion and it's older. I need to match the server config on my dekstop (Win7) and hosting server.

According to the logs, apache is getting error 13, which apparently means it does not have permission to view the files in the vhosts DocumentRoot. The config is fine and contains a specific Directory block for the doc root.

I've used chmod to change the permissions on the doc root to 755, but still get the same issue. The only thing that I can think is that as the root is inside my home dir the daemon user is not permitted access regardless. At this point, my understanding of linux users / groups starts to crack..

So - document root is :

/home/ben/Sites/ARC/site_dev/server_root/htdocs

Currently, 'ben' is the owner, 'ben' the group, and file permissions are set by chmod to 777. I know that's a bad idea, but I need to open it all to try to find the issue!

Is this an onwership issue? Can you specifically set permissions for the daemon user or group? Should I transfer owner to another user?

Help!!

Thanks  - B

---

### Post by Narkboy on 2010-08-19
Solved. All parent directories must be searchable - chmod -R +x /home/ben does it. Not sure if I've just driven a bus through the security, but not to worried. :)

---


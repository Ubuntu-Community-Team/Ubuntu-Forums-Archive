---
title: "Desktop to server"
date: 2008-12-04
forum: Desktop Environments
---

### Post by provomike on 2008-12-04
I have a bit of a dillema. I am going to order the Dell desktop unit with the quad dual core processor which comes with Ubuntu desktop. The problem is I am going to run a in house web server, ftp server, as well as virtual box on the system. I may even add a second network card and use it has a gateway. I know, a lot of functions on one machines but it will be heavily beefed up with max ram and 1 TB of disk space.

I have tried loading web services and such on the desktop but it argues with me. I want all the GUI features of the desktop plus the server functions. Can I just upgrade to the server version or will I have to do a fresh install?

Thanks!

---

### Post by ibutho on 2008-12-04
Personally I would do a fresh install of the server version along with a minimal GUI interface or webmin (a tool for remote administration via a web browser). I think installing a full desktop environment is unnecessary on a server because you will end up with a lot of apps that should not really be on a server and these can introduce potential security holes.

---


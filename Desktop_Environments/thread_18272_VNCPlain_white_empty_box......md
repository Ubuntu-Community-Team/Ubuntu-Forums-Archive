---
title: "VNC/Plain white empty box....."
date: 2005-03-05
forum: Desktop Environments
---

### Post by FX on 2005-03-05
I have Ubuntu running on a monitorless server. I have vncserver running on it. I can connect to it, but all I get is a plain white box and no desktop. The cursor is just a black dot and I can't right or left click on the screen. I had vncserver running just fine on it at one time, but I'm not sure what happen.

The server is running Warty and I can't get a desktop either from a windows machine or another linux machine.

Any ideas? 

Thanks ahead of time.

---

### Post by FX on 2005-03-05
Forget it I figured it out.

I have vncserver installed. Well all the while I was trying to connect I kept using the right ip address EXCEPT for the :2 after the address, which is the number of the vncserver. As soon as I put the :2 after the ip I got the regular desktop and everything works great.

Sorry for the dumb post.

---


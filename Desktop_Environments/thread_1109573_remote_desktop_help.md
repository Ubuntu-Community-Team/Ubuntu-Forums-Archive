---
title: "remote desktop help"
date: 2009-03-28
forum: Desktop Environments
---

### Post by mikedmor on 2009-03-28
I have some friends that really need help on their pc but they live very far away. i have tried to call them and use instant messenger to help but they just dont understand.

So i thought i would try to take control over their computer. What would be the easiest way of accomplishing this? remote assistance is only well remote. i need something that will let me do it over the internet

Also please keep in mind that he is very, uhh well nicely computer illiterate, so i need something that is very easy for him to setup. If its a little difficult on my end i can handle that.

Thanks

-Mike

---

### Post by pytheas22 on 2009-03-28
VNC is probably the simplest solution.  If your friend uses Ubuntu, he can enable it simply by going to System>Preferences>Desktop Sharing.  If he uses Windows or OS X, he will need to install a VNC client, like [tightvnc]("http://www.tightvnc.com/").  From Ubuntu, you can access his desktop (no matter which operating system and VNC client it uses) by going to Applications>Internet>Remote Desktop Viewer.

The only potentially difficult thing to configure on his end is the firewall if he's behind a router (or if his operating system has a firewall).  This isn't too hard to do, but the exact steps depend on which kind of router he has.  In most cases, he would access his router's configuration page by going to 192.168.1.1 in his web browser and configuring the router to forward connections on port 5900 (default VNC port) to his computer.  The other option is just to have him plug his computer directly into the Internet, taking the router out of the picture, although I wouldn't want to do that with a Windows or Mac machine because of security concerns.

There might be better solutions, and possibly ones that wouldn't require your friend to configure his router/firewall, but I'm not positive.  Hopefully someone else has better advice.

---


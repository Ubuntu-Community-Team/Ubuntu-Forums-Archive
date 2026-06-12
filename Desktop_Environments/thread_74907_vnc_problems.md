---
title: "vnc problems"
date: 2005-10-13
forum: Desktop Environments
---

### Post by urbanride on 2005-10-13
so i got it my client to connect to the unbuntu box,  but the menus appear and then quickly disapear so that i cant use them:confused:

---

### Post by HermanAB on 2005-10-13
If things are eratic, try using less colour depth.

See this guide, it may help:
[http://www.aerospacesoftware.com/vnc-howto.html](http://www.aerospacesoftware.com/vnc-howto.html)

Cheers,

Herman

---

### Post by urbanride on 2005-10-13
tried ... its really not a bandwidth issue ... i mean i am on an a lan

---

### Post by HermanAB on 2005-10-13
Long ago, there was a server side gpm bug that caused this to happen, but I don't believe that it can be the same problem anymore.  Other bugs affected the clients.

You should try to figure out whether the issue is on the client side or server side.  On the server, try to connect to itself and see if the problem occurs.  On the client side, try a different VNC client and see if it changes things.

Cheers,

Herman

---


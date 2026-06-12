---
title: "Jaunty and Webdav davfs etc"
date: 2009-04-24
forum: General Help
---

### Post by kevindontenville on 2009-04-24
I have upgraded to Jaunty (32bit) and thought that as the option for https connection was re-established for webdav that I would see how it worked.

However, I dont seem to be able to connect to any webdav service. Tried the test.webdav.org servers and got nowhere. Tried our own Zimbra servers still nothing.

When I say nothing I mean that it requests authentication or states the service is not available depending on whether I go through Nautilus go to or the connect to server route.

I reconfigured davfs to allow unprivileged users to mount via that but it is not the best solution for me really as I want more adhoc access. 

Anyone else show that they can connect to the test.webdav.org servers using Jaunty/Gnome? It would be nice to know its something wrong with my setup rather than a bug :)

---

### Post by jay76 on 2009-04-30
To add my experiences (in 9.04): I had similar problems with connecting to a webdav-enabled server through the "Places->Connect to Server" route - the damn thing wouldn't connect and kept returning a "HTTP: Unauthorised" error.

However when I opened a Nautilus window and changed the filepath display to editable (ie: not the button-style breadcrumb), and entered something like "dav://servername:8080/webdav" I was able to connect.

Interestingly (perhaps for me, but not the OP) it doesn't work with the examples given at test.webdav.org.

---


---
title: "Listen on a part"
date: 2009-01-11
forum: General Help
---

### Post by Black Mage on 2009-01-11
I did a netstat -an | grep LISTEN on my server to find out which ports are open. I am writing a program and need to open up my server to listen to a port. So how can I open a port up so it looks something similiar too:

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN

---

### Post by heindsight on 2009-01-11
That depends very much on what programming language you are using. If you're using C, you could install the manpages-dev package and have a look at the man pages for accept(2), bind(2), inet(3), listen(2), socket(2), tcp(7) and perhaps some of the other man pages referenced in those.

The basic idea is to create a socket, bind it to an address (port, ip-address combination) and then listen for connections on that socket. You 
call accept to wait for and accept a connection.

---


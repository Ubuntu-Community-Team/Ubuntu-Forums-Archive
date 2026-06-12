---
title: "ssh stops responding"
date: 2008-09-10
forum: Desktop Environments
---

### Post by MPD.JHB on 2008-09-10
I have a problem where SSH suddenly stops working.
I can ssh into a remote kubuntu 8.04 PC successfully.
I then close some of the connections, and leave a few open.

Subsequent attempts to SSH back into the same remote PC fail - either with a very long pause and then a connection error, or just "hangs".

One "client" uses ssh keys to auth, another does not.
The client NOT using ssh keys will be prompted for a password, after which it will "hang".

During this time, Apache will still server pages from the "server", I can connect to a mysql server on that PC using mysql -uroot -p -h[IP], I can ping the "server", I can telnet into port 22 (replies that it is a SSH service), BUT I cannot ssh in.

Any help or advice appreciated.

---


---
title: "Wvdial connects to ISP, but cannot ping (or otherwise access) the net"
date: 2005-12-16
forum: General Help
---

### Post by randcoop on 2005-12-16
Working with a dial up modem.  If I dial out using KPPP, the program crashes with a segmentation fault.

So I dial out with wvdial.  Does the handshake, logs in to the ISP, identifies local IP, remote IP, and primary and secondary DNS IP's.

Seems fine.  But nothing happens.  Trying to ping gets me unknown host or network unreachable errors.  I SEEM connected to the Net, but can SEE the net.

When I disconnect, it tells me how long I've been logged on for.

Can anyone help me use the connection that I appararently have?

---

### Post by jferrando on 2005-12-16
Try typing
**$ sudo ifconfig**
and see what interfaces shows.

---

### Post by randcoop on 2005-12-17
I get ppp0, with the local ip address matching the one assigned by the ISP.

---


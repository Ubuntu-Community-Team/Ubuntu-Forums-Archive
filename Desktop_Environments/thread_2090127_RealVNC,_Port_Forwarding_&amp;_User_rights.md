---
title: "RealVNC, Port Forwarding &amp; User rights"
date: 2012-12-01
forum: Desktop Environments
---

### Post by Waqar Azeem on 2012-12-01
I have installed RealVNC on Ubunut 12. And on the router configured the port forwarding. I used the default administrative user created at Ubuntu installation time.

Now Created few more users and run the VNC for each user in its session using su command.

These user can connect to their remote desktop, if they are on the same LAN.

If they come from remote site and pass through the router then they get Connection timed out (10060) error.

On test page [http://www.realvnc.com/cgi-bin/nettest.cgi](http://www.realvnc.com/cgi-bin/nettest.cgi) I get > Connecting to port 5900 ... succeeded.
Waiting for server to send version string... failed: [Errno 111] Connection refused


Two interesting observations are
* the user who configured the RealVNC server can access his remote desktop form out side the network easily.
* i stop all the vnc instances and rerun from each user this time online the user running on :1 is able to connect.

Any idea or guide line plase

/Waqar

---


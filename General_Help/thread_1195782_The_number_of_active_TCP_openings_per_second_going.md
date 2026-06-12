---
title: "The number of active TCP openings per second going up"
date: 2009-06-24
forum: General Help
---

### Post by valmarmoritz on 2009-06-24
Hi!

Can anyone explain or help me to investigate why "The number of active TCP openings per second" as shown by munin (see attached screenshot) has started to grow continuously.

---

### Post by jonobr on 2009-06-24
Hello

I have not used munin before but it looks interesting...

I normally stick with SNMP monitoring tools.

I cant really make out whats going on in the picture as the image is not 100% clear, however, I was wondering is it possible that this is a cumulative counter you are view and not an instantaneous one?

Can you verify this by using netstat to see if the number of TCP established sessions is increasing?
Are these all on the same port? or TCP sessions on different port number?

---

### Post by Brandon Williams on 2009-06-24
Try running 'sudo netstat -antp'. This will tell you the program associated with all TCP connections on the system. Are there any sockets associated with programs that you aren't not running yourself?

---

### Post by valmarmoritz on 2009-06-25
> **Brandon Williams said:**
> Try running 'sudo netstat -antp'. This will tell you the program associated with all TCP connections on the system. Are there any sockets associated with programs that you aren't not running yourself?
Thank You, fellows,

'sudo netstat -antp' showed a list of some 60 open tcp connections, most of them used by ktorrent. When I closed ktorrent, the list was quickly reduced to 13 ports being listened to + some 15 ports with different other statuses. All by programs I know and have authorized to run (boinc, firefox, gnome-panel, vmnet-natd, smbd, skype).

However, munin continues to increase the gauge of "The number of active TCP openings per second". This really does seem to be a problem of reporting rather than the actual net activity. Will try to dig further, if You can point me where to look next.

---

### Post by Brandon Williams on 2009-06-25
Try using tcpdump to just monitor syn packets. Something like this should work: 'sudo tcpdump -i any "tcp[tcpflags] == tcp-syn"' This will tell you a few things: Are the connections in question outgoing or incoming? What service are the connections going to? and Are there really as many connection attempts as munin says there are?

You could expand the tcpdump filter in order to figure out whether the connections are being accepted and, if so, how long they stay open. This would do it, I think: 'sudo tcpdump -i any "tcp[tcpflags] & (tcp-syn|tcp-fin|tcp-rst) != 0"' This would allow you to see the SYN packet, the SYN-ACK or RST packet sent in response to the SYN, and the FIN and RST packets sent to shut down established connections.

---

### Post by jonobr on 2009-06-25
Hello


Sounds like you have found the issue,
Im not torrent expert, but with ktorrent,

are other peers downloading from you and as such opening ports also?
IF so can you limit that number of sessions allowed to your system?

---


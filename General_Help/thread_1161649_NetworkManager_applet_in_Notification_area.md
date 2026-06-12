---
title: "NetworkManager applet in Notification area"
date: 2009-05-16
forum: General Help
---

### Post by rbc on 2009-05-16
I have a Jaunty laptop with two user accounts. I have administrative rights and the other user has desktop privileges. When logged on as myself, the NetworkManager applet does not show up in the Notification area of the top panel. For clarification, it is the wireless signal strength icon. Wireless connects just fine, but I am getting ready to go on vacation, and right clicking on the icon will allow me to scan for the hotel's wireless network. How do I add this?

---

### Post by x33a on 2009-05-16
check if system -> preferences -> startup applications -> network manager is enabled.

---

### Post by rbc on 2009-05-16
It was enabled, BUT Options/"Automatically remember running applications...." was not checked. I checked that and all is well. Thanks

---

### Post by rbc on 2009-05-17
I realize I am probably cluttering up the forum but I wanted to post my findings in case anyone was looking at this thread for an answer to a similar problem. I was premature in saying that the actions I previously took had solved the problem. I did, however, discover  why the applet was not showing up. The first user to log on seems to get the network manager applet. In other words, after a Shutdown and restart, Restart, or all users logging off.....the first user to log on gets the applet in his Notification area. Any subsequent users to log on do not. I guess the rationale behind this is that why should a second user try to log on to another network when a perfectly good one is already available and connected......or......the second user cannot, or shouldn't, try to log on to a second network using the same NIC. Again, sorry if I am stating something was obvious to everyone else or if I am completely wrong in my assumptions, but I hope this helps someone else's frustration. And I welcome any constructive criticism.

---


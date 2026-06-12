---
title: "Remote printing"
date: 2011-09-14
forum: Desktop Environments
---

### Post by Clary on 2011-09-14
p { margin-bottom: 0.08in; }  Hi guys!!!
 I'm really sorry if my thread is off topic but I need help.  
 The thing is I work in a remote desktop and I need to print documents from time to time, but my stupid printer doesn't print. It works on my home computer but not in the remote session. I'm tired of copy-from-server-past-to-workstation stuff.... If someone knows how to fix it, please tell me!!!!  
 

 Clary

---

### Post by Lisiano on 2011-09-14
1) If both systems are on Linux
Connect to your home PC from the remote session
```
ssh -L 1631:localhost:631 home-pc.ip
```
Or if you are port blocked on your home PC.
```
ssh -R 631:localhost:1631 server.ip
```
Then go to [http://localhost:1631/](http://localhost:1631/) on the remote machine, find the printer ([http://localhost:1631/printers/Some-printer](http://localhost:1631/printers/Some-printer)) and copy the URL. Then go to System -> Printing and add the printer in Other

2) If server is on Windows
On the server, download PuTTY or any other SSH client with port forwarding and SSH to your home PC and port forward port 631 on the remote machine to port 1631 on the local machine then once again find the printer as above and add the printer via the Windows Network Printer or what it's called.

Hope this helped.

EDIT: You need to enable network printing from inside the CUPS administration panel ([http://localhost:631/](http://localhost:631/)) or in System -> Printing or this won't work.

---


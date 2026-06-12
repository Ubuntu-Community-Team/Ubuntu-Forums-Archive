---
title: "Remote Access"
date: 2007-11-17
forum: Desktop Environments
---

### Post by marcadams on 2007-11-17
Hello - I am about to switch my mother to Ubuntu. However she doesn't live all that close. So in an attempt to reduce the number of times I have to visit her to sort out any issues, I was wondering what the best remoting software would be?
What ever the software, I need to be able to connect to her machine, without asking her to do much.

I look forward to your advice. Many thanks !

---

### Post by x64Jimbo on 2007-11-17
Set up SSH and VNC servers on the machine. Firewall the VNC port from the outside, but leave SSH open. When you need to see her screen, tunnel your VNC connection into her machine. There is an option in tightvncviewer to tunnel through SSH. This makes your communication with her machine secure and leaves it less open to some of the more common VNC exploits.

---


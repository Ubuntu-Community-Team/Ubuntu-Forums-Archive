---
title: "issues with 2 webapps"
date: 2006-01-01
forum: General Help
---

### Post by qferret on 2006-01-01
I have 2 web based applications that I would like to be able to access from my Ubuntu box.

The first is a java webstart application that allows me to connect to Citrix Web access where I work. The webstart app starts fine, but when I try to get to any of the items on the list that comes up, it tells me that it can't create the SecureTunnel as port 80 is in use.

Netstat shows nothing on 80. Ethereal shows no activity on 80. I ended all services I could and killed all unnecessary processes. Same result.

I used to dual boot this machine, and I could get in from the XP partition, so it's not hardware or network. Firing up an XP VM on top of Ubuntu gives the same error, so it seems that Ubuntu is indeed locking the port with something.

Any pointers on how to track down the culprit would be appreciated.

The 2nd app is WebCT. Linux in general isn't supported, but there are people who have gotten it to work. When I log in, it says my logon information is invalid. Entering the same info on my work laptop (XP) gets me right in. I find it humorous that I need to run on Windows to access online ComSci courses  ;-)

Any pointers on this one (such as what information would even be helpful) would also be appreciated.

---

### Post by qferret on 2006-01-03
No takers? Not even on the first one (port 80 in use)?

---

### Post by qferret on 2006-01-08
[sarcasm]
First, I'd like to thank everyone for their invaluable help.
[/sarcasm]
:rolleyes: 

Seriously though, apparently either the university upgraded the WebCT software or an Ubuntu update fixed it. I can now log onto WebCT with no issues. 

The port 80 in use on the Java WebStart app still has me stumped though.... no advice from anyone on what to look for?

---

### Post by qferret on 2006-01-16
*bump*

---


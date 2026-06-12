---
title: "Router Issues"
date: 2009-05-24
forum: General Help
---

### Post by KGF2009 on 2009-05-24
Hey, I have Ubuntu 9.04 and I'm trying to host a website from it, but I have to go through a router. The router is a Linksys BEFW11S4.
I can access the website from 127.0.0.1, 192.168.1.100, and localhost, but when I try the actual IP, it just doesn't load, and times out. I have forwarded port 80 from my router to my computer, so I have no idea what's wrong. Any help?

---

### Post by Kareeser on 2009-05-25
From what you said, it should work... I'd check the apache config files to make sure you're allowing access from outside of the local subnet.

---

### Post by KGF2009 on 2009-05-29
It's set to allow anyone in. What's wierd is, it worked fine before and then it just quit. ...I wonder if this has anything with me upgrading to 9.04..?

---

### Post by cariboo on 2009-05-29
To make sure you have port 80 forwarded properly check [canyouseeme]("http://www.canyouseeme.org/").

---

### Post by ActiveFrost on 2009-05-29
Apache haven't changed anything .. I've a server + router and everything works just fine ( router:80 forwarded to local:80 ). You should take a closer look at your router settings ( Virtual Server or whatever it's called in LinkSys ) ;)

---

### Post by KGF2009 on 2009-05-29
I checked that site, and when I clicked Check, nothing happened. Does that mean it didn't work? And I've checked my router settings many times.

---

### Post by TransitMan on 2009-05-30
I just went to the site indicated and got a detail explaination of what ports may be blocked by ISP's, including PORT 80.
You may have to use a different port to attain what you need, or use No-IP.com for a solution.

---

### Post by KGF2009 on 2009-05-30
Actually, at the moment I'm trying to use DynDns, but obviously I get the same problem as when I try the IP itself. And..How would I change what port apache listens on?

---


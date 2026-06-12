---
title: "GNOME 3 security"
date: 2011-07-04
forum: Desktop Environments
---

### Post by Anders H on 2011-07-04
Hi guys, 

Hopefully this is not the wrong location for this thread, nor an overly stupid question but I've been wondering about some thing that I heard about GNOME 3. 

Now GNOME 3 is supposed to be mostly Java script right? Now maybe this is a hold over from my Windows days of being scared of viruses around every corner, but does this pose any kind of security risk to my system? I know there are a few cross platform attacks that use Java or Flash. 

Yes I know that it is very difficult for malware to run on any Linux OS due to the permissions. But I'm paranoid and when I hear that a UI, even a Linux one is mostly Java I start to wonder. 

So in short is there any reason to be concerned about running GNOME 3 and being exposed to attacks. 

Thank you in advance.

---

### Post by 3Miro on 2011-07-04
JavaScript in Gnome-shell has very little to do with JavaScript on the Internet.

On the Internet, JavaScript is part of a web-page. When you visit that web-page, your browser executes the JavaScript on your machine. If JavaScript is malicious, your browser is supposed to catch it, but it may fail.

Also, JavaScript is completely different from Java or Flash. The common attacks are for Java and Flash, but all of those require you to get something off the Internet.

Gnome-shell doesn't connect to the Internet, all the code stays on your machine. Using JavaScript in Gnome-shell is no more secure or unsecure than using C++ or any other language.

---

### Post by Anders H on 2011-07-04
Thank you for the explanation. It kind of seems like a "duh" now but thank you for explaining that to me. :lolflag:

---


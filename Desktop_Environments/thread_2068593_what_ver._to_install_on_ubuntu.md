---
title: "what ver. to install on ubuntu"
date: 2012-10-09
forum: Desktop Environments
---

### Post by workaround on 2012-10-09
I would like to interface java to mysql on ubuntu. Would anyone have any suggestions what version of mysql should I install on ubuntu. It is not for commercial dev only to mess around and see what's possible. 
 Thanks.

---

### Post by snowpine on 2012-10-09
Generally speaking I would recommend installing the stable, tested, and trusted version that's in the repositories for your Ubuntu release. Is there a reason you want/need to install a different, unsupported version?

[https://help.ubuntu.com/12.04/serverguide/mysql.html](https://help.ubuntu.com/12.04/serverguide/mysql.html)

---

### Post by workaround on 2012-10-09
"Generally speaking I would recommend installing the stable, tested, and trusted version...", well, which one is that then?
Thanks for the link, part of what I am looking for.
Thanks.

---

### Post by snowpine on 2012-10-09
Since I am not a mind-reader I don't know which Ubuntu release you are running. Each Ubuntu release uses whatever mysql was stable at the time it was released.

To find out the available version of any package you can use "apt-cache policy":

```
apt-cache policy mysql-server
```

Apologies if I overestimated your Ubuntu experience. Here is a how-to that covers the basics of installing software in Ubuntu: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by workaround on 2012-10-09
mysql-server:
  Installed: (none)
  Candidate: 5.5.24-0ubuntu0.12.04.1
  Version table:
     5.5.24-0ubuntu0.12.04.1 0

---

### Post by snowpine on 2012-10-09
That's a pretty good version, go for it! :)

---

### Post by workaround on 2012-10-09
OK, I am going to install "Mysql server"! Thanks.
 

 In regard to your comment; “Apologies if I overestimated your Ubuntu experience ...”, I did not have to do anything except downloading it twice that fixed the initial problem with my resolution and reconnect my mouse, just flawless experience otherwise.

---

### Post by snowpine on 2012-10-09
Since you mention "screen resolution and mouse" I'm assuming this is a desktop, not a server, install?

In that case you don't even have to use terminal commands if you don't want, you can use the point-and-click Ubuntu Software Center as described here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by workaround on 2012-10-09
Yes, it is desktop.
  	 	 	 	 	 	   OK, there are three versions of it: 1) **Development Libraries, 2) Client Utilities, and 3) Test Suite  in 32 bit. Do I need all of them or should I need only the (2).**
 **Thanks.**

---

### Post by snowpine on 2012-10-09
> **workaround said:**
> Yes, it is desktop.
  	 	 	 	 	 	   OK, there are three versions of it: 1) **Development Libraries, 2) Client Utilities, and 3) Test Suite  in 32 bit. Do I need all of them or should I need only the (2).**
 **Thanks.**

Since your stated goal is to "mess around and see what's possible" only you can answer that question. Each of those packages you mention has its purpose and if that's something you want to mess around with then go for it. 

If your goal is specifically to create MySQL databases then I recommend you install the package **mysql-server** and follow the how-to I linked in post #2.

---

### Post by workaround on 2012-10-09
found it! I am impressed! Such a nifty fancy implementation! I had to search for it since it does not show up but all is right there.
 Thanks much!
  :guitar:

---


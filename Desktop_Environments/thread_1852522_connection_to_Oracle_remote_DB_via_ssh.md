---
title: "connection to Oracle remote DB via ssh"
date: 2011-09-30
forum: Desktop Environments
---

### Post by kasans on 2011-09-30
Hello,
Could anybody suggest me any GUI software to connect to remote Oracle DB 10g via SSH. But it should not be running in WINE environment - not a Windows app..
And it would be pretty good if you share your experience of installation/configuration of the software

Thank you in advance...

---

### Post by lykwydchykyn on 2011-09-30
What version of Oracle?

10g and later have a web interface; you could conceivable set up an [ssh tunnel](http://www.revsys.com/writings/quicktips/ssh-tunnel.html) to the port running the web interface and use that (been to long since I messed with Oracle, I don't remember the port number).

I guess you could do the same (ssh tunnel) for older versions, just using the Java client (oemapp console) or tora.

---

### Post by kasans on 2011-09-30
thank you, [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141") for your response. It could be good option, but I guess my oracle doesn't have Java interface installed. [http://x.x.x.x:8080/apex](http://x.x.x.x:8080/apex) gives me an error page...
Is there any other solutions?

---

### Post by lykwydchykyn on 2011-09-30
What version of Oracle are you running?

I've used 9i and 10g, but I don't remember port 8080 or anything about apex.

---

### Post by kasans on 2011-10-03
> **lykwydchykyn said:**
> What version of Oracle are you running?

I've used 9i and 10g, but I don't remember port 8080 or anything about apex.


It is 10g.

from sqlplus prompt:
"Oracle Database 10g Enterprise Edition Release 10.2.0.3.0 - Production
With the Partitioning and Data Mining options"

---

### Post by Waappu on 2011-10-05
Hi,

You open SSH tunnel to your database SQL net port (default port is 1521).

You can use e.g. SQL developer as client
[http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html](http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html)

When specify connection to SQL Developer use "localhost" as hostname

---

### Post by kasans on 2011-10-05
> **Waappu said:**
> Hi,

You open SSH tunnel to your database SQL net port (default port is 1521).

You can use e.g. SQL developer as client
[http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html](http://www.oracle.com/technetwork/developer-tools/sql-developer/overview/index.html)

When specify connection to SQL Developer use "localhost" as hostname


Thank you!!!:KS

---


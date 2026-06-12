---
title: "Opening port"
date: 2009-04-15
forum: General Help
---

### Post by kristian_nissen on 2009-04-15
How do I open a specific port?

If I telnet telnet 127.0.0.1 21822 I get a:

Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

How do I open up the port? It's not showing up on netstat -l

---

### Post by Alekz_ on 2009-04-15
Hi kristian! :)

Take a look in these files:

/etc/inetd.conf

and

/etc/services

These files have the service/port of you system!

[]'s

Alekz_

---

### Post by kristian_nissen on 2009-04-15
thanks

cat /etc/inetd.conf is empty

what should I bee looking for inside cat /etc/services ?

---

### Post by sahabcse on 2009-04-15
Hi


Type the bottom of your /etc/services

ex)
zimbra-apache 8080/tcp
zimbra-apache 8080/udp

Here we have opened the port 8080 for zimbra-apache service

Then try 

#telent localhost 8080

If it is connect means try from external server.

For knowing the port status 

#nmap localhost

---

### Post by Alekz_ on 2009-04-15
Well.. I don't know "what" your are looking for.. :)

You ask how to open a port, so I told you that there are some files that tell the system that port x, y ... n are open, with the protocol X and so on...

Take a look at this:
[http://www.faqs.org/docs/securing/chap5sec36.html](http://www.faqs.org/docs/securing/chap5sec36.html)

It may help you to understand how it works...

Just a question.. What do you want exatly? Just to change the telnet port? If it is, I'm telling you a lot of unnecessary things! :) hehe

[]'s

Alekz_

---

### Post by kristian_nissen on 2009-04-15
I'm working on a PHP based app where I have to post data to an external service using that port

---

### Post by The Cog on 2009-04-15
They almost certainly mean that you post to their port 21822, rather than opening your port 21822. A port is open when there is an application listening for incoming connections on that port. So the reason you get connection reused when you try to connect to your own port 21822 is that you haven't started anything that listens for connections on it. 

If their address is thingy.wotsit.com, then try posting your data to thingy.wotsit.com:21822.

---


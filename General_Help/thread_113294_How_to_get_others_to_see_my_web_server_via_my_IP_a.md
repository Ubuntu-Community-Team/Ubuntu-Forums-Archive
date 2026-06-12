---
title: "How to get others to see my web server via my IP address?"
date: 2006-01-06
forum: General Help
---

### Post by jrs1985 on 2006-01-06
I'm using XAMPP right now and I want others to be able to see the stuff in my htdocs folder by simply using my IP address. They can't see it and I'm not sure why. PLEASE HELP! I'm sure the solution is simple.

Is it possible w/o domain name? I would think surely it must be.

---

### Post by DaMasta on 2006-01-06
Yes, they need to type in your external ip address. You have apache running?

---

### Post by jrs1985 on 2006-01-06
I think so. I went to "ifconfig" and used the "inet addr"

should i use the Bcast?

Also, I have 2 connections on my router, both via ethernet cables, does this matter?

I also tried SLAMPP to see if I could do the server thing & it still didn't work out. Error 500 on both. Is it just my internet company (time warner)?

---

### Post by DaMasta on 2006-01-06
If you have someone trying to access it from the outside, go to [http://www.whatismyip.com](http://www.whatismyip.com) to get your external ip. Then type sudo apache2ctl start. If you have a firewall up, you need to open port 80, or the http port.

---

### Post by hw-tph on 2006-01-06
First step should probably be to check if it works from your local machine: Type in [http://localhost](http://localhost) in the location bar in Firefox and see if can see it yourself.


H&#229;kan

---

### Post by Haegin on 2006-01-06
You need to set up forwarding on your router so that all connections on port 80 (TCP) are forwarded to port 80 on your computer (using your local ip address). Also make sure you have a static local ip address. Check [http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm) for info on setting it up.

---

### Post by ptmurphy on 2006-01-06
There are several things you need to make sure are working, and some of them have been outlined above.

1. Make sure your web server is up and running.

2. Make sure you can get to the web pages from your local machine by typing "http://localhost" and/or "http:127.0.0.1" in your browser address bar.

3. Are you connected directly to the Internet or through a router?  If you are using a router, you will need to know your EXTERNAL ip address, which is the address the router reports on the internet side.

4. Once you know that IP address, you will need to set your router to "forward" port 80 requests to the correct INTERNAL ip address (the address you computer is reporting).  Most routers call this "Port Forwarding" or something similar.  You would tell the router to forward port 80 requests (standard http port) to the computer that is running the web server (typically something like 192.168.0.2).

5. More than likely your Internet Service Provider will periodically change your external IP address (renew you lease on that number).  If this is the case, the address your friends use would change anywhere from every couple of hours to once a month.  To get around this, there is a free service called DDNS (Dynamic DNS).  You can get there at [www.dyndns.org](www.dyndns.org).  This service will allow you to register a free domain (within certain sub-domains) and have your router automatically update your IP Address when it changes.  Most routers support this functionality.

If your router does support this functionality, your friends would enter a name, such as xxxxx.is-a-geek.com instead of an address to reach your web server.  Your router will have to be setup to login to your account every time your IP address changes and update the address at DynDNS.  I have been using this for years and it works great.

Hope this helps.

---

### Post by Haegin on 2006-01-06
Please note that some ISPs block commonly used ports including port 80. I am currently trying to set up my forwarding and I'm having problems... If this is the case you could try setting the ip for dyndns to be <external ip address>:<another port>
For example: 212.74.112.66:9556 (note - thats a tiscali dns - make sure you change the ip... (it was the first thing that came into my head that didnt start with 192.)
(Note - 9556-9592 are unassigned according to a port number list thing I have attached).

You then need to forward this new port to port 80 on your computer.

---

### Post by sempoii on 2006-02-12
sorry im completely noob at this.
what is externel and internel IP address?.

if i check my IP at cmyip.com , what is it? is it external or internel?

---

### Post by Haegin on 2006-02-12
Your internal IP address is the address you use on your local network. There is one per computer. Your external ip address is the address you are seen as on the internet. For somebody on your network (probably inside your house) to connect to your pc they need to use the internal ip address. For somebody else (i.e. a friend connecting over the internet) to view your site they need to use your external ip address. Port forwarding may be needed if you have a router otherwise the router will get the request for the web page from your friend and will not know which computer on your network to pass it along to.

I hope this helps a little

---

### Post by sempoii on 2006-02-13
so it's my external ip address that i see at cmyip.com
i got it. thank you.

---


---
title: "Apache2 opening up a lot of processes when i &quot;refresh&quot; page"
date: 2009-04-02
forum: General Help
---

### Post by champi0n on 2009-04-02
When I press f5 a bunch of times, or hold down f5 to refresh the page, it ends up displaying a blank page and then constantly spinning the loading icon.

When i check my server (2 x quad core xeons with 16gb of ram), it shows a TON of apache processes and a system load of about 50-60. (This is of course when i wait 10 minutes for the command to show up).

Now I might expect apache to launch separate processes for different clients maybe, but not from just refreshing the page!

It's pretty much a default install with nothing extra configured in apache other then some basic vhost files.

---

### Post by champi0n on 2009-04-03
I've tested on my CentOS boxes and the maximum apache processes it opens is seven or so. So I guess ubuntu isn't really set out to be a server or what?

I use ubuntu on my home desktop, work desktop, home media server, and a production web server that holds 3 of my websites.

I use CentOS on 3 production shared hosting servers with some pretty decent traffic. And no problems to report.

Why does my 1 ubuntu server with overkill specs suck so bad? I refresh the webpage for all of 5 seconds and a million (maybe 2 million) apache processes pop up and go defunct.... allowing the server load to top out in the 60.0 + range.

---

### Post by firefly2442 on 2009-04-04
Are you trying to do a benchmark?  If so, apache already has a tool builtin:

[http://httpd.apache.org/docs/2.0/programs/ab.html](http://httpd.apache.org/docs/2.0/programs/ab.html)


As for refreshing, if you look in the /etc/apache2/apache2.conf configuration file, you'll probably see something like the following:

> 
StartServers          5
MinSpareServers       5
MaxSpareServers      10
MaxClients          150
MaxRequestsPerChild   0


This tells the server how many processes to start (essentially waiting for a connection) and other details.  You might want to check that these are set correctly.  Perhaps apache is spawning too many processes?  Other things you might want to take into account are databases.  If your main page is accessing a database then it might be creating separate threads for each connection.  Anyway, hopefully this will give you a little to go on.  Good luck. :)

---

### Post by champi0n on 2009-04-04
Hey thanks for the reply,

I wasn't benchmarking, I was just pressing F5 to see if i could see my custom CSS loader graphic show up before an image.... and then the server "crashed" so to speak.

It's a single static html page with 2 images.

I figure its easier to just install a different distro on another server and then migrate all my data over at this point.

---


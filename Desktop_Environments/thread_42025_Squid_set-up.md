---
title: "Squid set-up"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-15
Does anyone know how to set up squid to allow ip address 192.168.0.2. to use the http and ftp proxys that make up the program. I can cope with a bit of code and text file editing, but have you seen the squid config file? 

I already installed webmin and it had no start icon and didn't run from terminal. Surely webmin can't control squid without a few hours config itself? 

I simply do not believe seting up a proxy is really this difficult. The config file should be csv (that's still text) and then it could be edited as a table in OOo

---

### Post by desdinova on 2005-06-15
XML would be a lot better then CSV, as XML makes a lot more sense - besides CSV is messy

This any use?

[http://squid-docs.sourceforge.net/latest/html/book1.html](http://squid-docs.sourceforge.net/latest/html/book1.html)

---

### Post by desdinova on 2005-06-15
[http://squid-docs.sourceforge.net/latest/html/x591.html#AEN595](http://squid-docs.sourceforge.net/latest/html/x591.html#AEN595)

"
**Example 3-2. Theoretical Access List**

 http_access deny 10.0.1.0/255.255.255.0
http_access allow 10.0.0.0/255.0.0.0
icp_access allow 10.0.0.0/255.0.0.0 Rule sets like the above are great for small organisations: they are straight forward.

 For large organizations, though, things are more convenient if you can create classes of users. You can then allow or deny classes of users in more complex relationships. Let's look at an example like this, where we duplicate the above example with classes of users:

---

### Post by Dave_is_sexy on 2005-06-15
ok i'm not going to get that. 

If there's no graphical front end (that works) 

and no tabe to edit in the config files

and no graphical proxy servers available for linux

and no graphical way to edit any built in IP tabels

then i would like to say "ALLOW ALL TRAFFIC" That CANNOT be more than 1 line!

I know there are risks, but it's tempory - no one's gonna find my IP and my lovely GRAPHICAL firewall seems to be ontop of that anyway - it has an INDICATOR to tell me that everything is ok on it's sensible DEFAULT settings

---

### Post by desdinova on 2005-06-15
[QUOTE=Dave_is_sexy]ok i'm not going to get that. 

If there's no graphical front end (that works) 

and no tabe to edit in the config files

and no graphical proxy servers available for linux

and no graphical way to edit any built in IP tabels

then i would like to say "ALLOW ALL TRAFFIC" That CANNOT be more than 1 line!

I know there are risks, but it's tempory - no one's gonna find my IP and my lovely GRAPHICAL firewall seems to be ontop of that anyway - it has an INDICATOR to tell me that everything is ok on it's sensible DEFAULT settings[/QUOTE]
 Webmin has a squid graphical module

 But the answers there

  http_access allow 10.0.1.0/255.255.255.0
 

replacing with your network range

---

### Post by desdinova on 2005-06-15
[QUOTE=desdinova]Webmin has a squid graphical module

 But the answers there

  http_access allow 10.0.1.0/255.255.255.0
 

replacing with your network range[/QUOTE]
 [http://www.webmin.com/](http://www.webmin.com/)

Webmin is installable via apt-get - its a web based config/admin tool

"
**What is Webmin?**

 * Webmin is a web-based interface for system administration for Unix.  Using any browser that supports tables and forms (and Java for the File Manager module), you can setup user accounts, Apache, DNS, file sharing and so on. * *  Webmin consists of a simple web server, and a number of CGI programs which directly update system files like /etc/inetd.conf and /etc/passwd. The web server and all CGI programs are written in Perl version 5, and use no non-standard Perl modules.*"

---

### Post by Takis on 2005-06-15
Dave, is your main computer your frontline computer?

It sounds like it is. If so, you may want to consider getting a dedicated firewall between your box and the Internet, such as [Smoothwall](http://www.smoothwall.org).

---

### Post by aglauser on 2005-06-15
[QUOTE=Dave_is_sexy]ok i'm not going to get that. 

<snip>
[/QUOTE]

Okay ... so if I understand correctly you do not understand this part from the documentation:

[QUOTE=desdinova]
 http_access deny 10.0.1.0/255.255.255.0
http_access allow 10.0.0.0/255.0.0.0
[/QUOTE]


What this mean is deny access to 10.0.1.* and allow access to 10.*.*.* (if it is not denied by the first rule).

The first part is the network addess ... in you case likely 19.168.0.0 or 192.168.1.0.  The second part is the network mask.  If you AND the IP address and the netmask, you get the network address:   192.168.0.1 AND 255.255.255.0 = 192.168.0.0.  To see why you have to convert the addresses to binary.

So, I hope this helps if you can't get webmin to work for you.


Edit:  Changed 'Shorewall' to 'Smoothwall'
BTW, Smoothwall is a pretty cool linux distro that you can install on an old computer and then use that computer as a router.  I tried it out and quite liked it.  The only downside is that an old PC probably draws a lot more power than your average purpose-built router.

Edit:  Shorewall, OTOH is a handy tool for making it easier to set up iptables.  It is also pretty handy but takes a bit more reading to get the hang of.

---

### Post by Takis on 2005-06-16
[QUOTE=aglauser]... then use that computer as a router.  I tried it out and quite liked it.  The only downside is that an old PC probably draws a lot more power than your average purpose-built router.[/QUOTE]
True, however your average purpose built router does no logging, no proxy, no filtering & no virus scanning (note: not part of a standard build) and (a couple I've seen) will tend to actively block packets rather than drop them. In short, your average router is totally blown away by Smoothwall. My main argument pro-Smoothwall though is that its primary purpose is firewall, whereas a router's primary purpose is routing.

---

### Post by Dave_is_sexy on 2005-06-16
Smoothwall sounds nice - but it's a dsstro? So... bye bye desktop and .deb installers?

My comp is the main one. It's directly connected to the net. On windows i've done this very securely (cos i understand it). On ubuntu there is currently no security, but there isn't really anything else either. I think they gave me OOo, Firefox, apt-get and gnome. 
And they even managed to ruin the icons for OOo and Firefox with their own crappy designs

I think i get the IP thing a bit better now. But Webmin doesn't do anything. Theres' no "shortcut" to start the GUI and typing it into terminal its' just like "yeah i've done that"

... i mean... where? Show me! bring up a window or print some fedback.

---

### Post by aglauser on 2005-06-16
First, find out if Webmin is running:

ps -A | grep webmin

(ps -A shows all processes, the '|' passes the output to grep, which filters out the lines that don't contain webmin).  If you get no output, then try:
[B]
sudo updatedb[/B]  (this updates the slocate database, which lets you easily search for files)
<wait a while>

when the prompt comes back, type:

**locate webmin | grep init**

you should see something along the lines of /etc/init.d/webmin.  What we are trying to do is find the start/stop script for webmin.  Once you figure out where that is, typing:
[B]
/path/to/script/webmin start[/B]

should start the webmin service.  There is probably a GUI tool to do this as well, but I don't know what it is - sorry.

Now that you have webmin running, to actually use it open up firefox and in the web address field type:

**[http://localhost:10000](http://localhost:10000)**

10000 is the default webmin port, if you webmin is running and you can't connect using port 10000, you might have to search the webmin.conf file (I'm assuming such a file exists) to find out which port it is using.

Now you should be ready to set up squid from a web-based GUI!


As for a firewall, I am with Takis in suggesting that a seperate router/firewall is a really good idea.  However, if you really don't want that, then Shorewall is a program that makes it somewhat easier to set up a firewall on your Ubuntu machine.  I'm pretty sure Ubuntu also has a GUI tool in the system menu which will allow you to set up a firewall.

HTH,

---

### Post by desdinova on 2005-06-16
Shorewall doesn't gui - but the Shorewall website gives you a sample two interface setup that you edit two files and then run it by

/etc/init.d/shorewall restart

---

### Post by desdinova on 2005-06-16
When you install webmin it starts as a service automatically - you then access it via 

[http://ip.address:10000](http://ip.address:10000) 

in your web browser as the other poster said

---

### Post by aglauser on 2005-06-16
[QUOTE=desdinova]Shorewall doesn't gui
<snip>
[/QUOTE]

Well, not natively, but there *is* a Webmin module:  webmin-shorewall in universe.  I would recommend reading the Shorewall docs though - pretty straightforward and it's good to understand what's going on with the firewall.

---

### Post by Takis on 2005-06-16
[QUOTE=Dave_is_sexy]Smoothwall sounds nice - but it's a dsstro? So... bye bye desktop and .deb installers?

My comp is the main one. It's directly connected to the net. On windows i've done this very securely (cos i understand it). On ubuntu there is currently no security, but there isn't really anything else either.[/QUOTE]
Yeah it's a distro, you put it on a totally separate computer, an old POS is the usual victim (I'm running it on a P350, but that's real overkill. A 486 or even 386 is good enough). It's a ~40meg download, you burn it to CD and then chuck the CD in the computer. The install is quite quick and easy, et voila you have your firewall. It definitely has a (web-based) GUI and everything (see attached).
IMHO, a dedicated firewall is more secure than a software based one (eg Shorewall) cause you're dropping bad packets before they even get to your real computer, amongst other reasons.

I'd be very interested to know how you think your Windows is so secure, if you don't mind, just out of curiousity. BTW Ubuntu doesn't come with any sort of security thing standard because on a base install there are no open ports.

---


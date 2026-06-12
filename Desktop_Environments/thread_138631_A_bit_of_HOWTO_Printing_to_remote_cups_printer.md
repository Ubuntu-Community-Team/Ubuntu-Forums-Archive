---
title: "A bit of HOWTO: Printing to remote cups printer"
date: 2006-03-02
forum: Desktop Environments
---

### Post by siennalizard on 2006-03-02
Hello all.

Hoping this will help someone out. As ever, post back if you don't understand what I'm talking about.

Your goal (if it's the same as mine) is to print remotely to your Ubuntu Breezy server, using cups and ipp.

Firstly, thanks to Joe_Lurker, we have his advice (from here: [http://ubuntuforums.org/archive/index.php/t-78976.html):](http://ubuntuforums.org/archive/index.php/t-78976.html):)

> 
Forgot one thing. The default setup on the Ubuntu machine does not make the printers available on the network. You will have to edit the /etc/cups/cupsd.conf file. Find the line "#Port 631" (about line 450) and remove the #. About 2 lines down there will be a line "Listen 127.0.0.1:631". Put a # in front of this line to comment it out. Next find the line "<Location />" (about line 796) and after the line "Deny From All" add a line "Allow From <network address/mask>" where network address is your network ip address - for instance 192.168.1.0 and mask is your net mask bit - for instance 24:
Allow From 192.168.1.0/24

save the file and restart cups:
sudo /etc/init.d/cupsys restart

Joe

Check that you can bring up a browser on the client, then surf to http://<hostname>:631. That should give you the cups manager, but you shouldn't have to change anything here.

Then we need to actually use the correct queue name. You need to spell it like this when you're setting up your printer on the client side:

ipp://<hostname>:631/printers/<print-queue>

The <print-queue> is the name cups gave your printer when you set it up on the server.

Let me know if you have any difficulties with this, or if I missed an obviously helpful source (or if this was actually helpful, not that I have ego problems, or anything...).

Best wishes,
J.

---

### Post by minghai on 2006-03-02
Hi,

   Your HOWTO looks like just what I need to get my little LAN of 4 machines to see each other's printers.  Just a couple of newbie questions:

1) How do I find out what my net mask bit is?
2) How do I find out what the print-queue (the name cups gave my printer when I set it up on the server) is?

   Thanks!

Ming Hai

---

### Post by siennalizard on 2006-03-02
I'm going to take a guess that you have a 192.168 style network. If so, it's likely that your netmask bit is 24 (that's equivalent to 255.255.255.0).

To see your ip, type ifconfig and look for the eth0 interface (if your machines are cabled up, not wireless). If wireless, look for eth1 or wlan0. You'll see your ip on the inet: line, along with your Mask.
So you'll need:
```
Allow From 192.168.2.0/24
```
for a Belkin. You could also use:
```
Allow From 192.168.2.0/255.255.255.0
```
as they're functionally identical.

To find out what your print queue is called, just look at the printer setup box on the host. The print queue is the printer name as displayed there.

Hope that helps!
J.

---

### Post by minghai on 2006-03-03
That works great, thanks!  Just one more thing.  I'm using DHCP, so does that mean my ip address will be different everytime?  If so, how should I change cupsd.conf?  Thank you.

Ming Hai

---

### Post by siennalizard on 2006-03-03
Shouldn't be a problem for two reasons.
Firstly, most routers give out the same ip to the same mac address every time. Secondly, what you've specified (correctly, I might add) is your _whole_ network: your router will always give out dhcp ip addresss in that range. The zero at the end of the ip address you should have given means "allow everyone in this subnet". So even if you're assigned 192.168.2.6 some days, and other days you log on wirelessly and get 192.168.2.121, you'll still be covered by that "Allow From" line.

Hope I've explained that well enough...!

J.

---

### Post by minghai on 2006-03-03
Yep, got everything working thanks to you J :-)

Ming Hai

---

### Post by pointym5 on 2006-03-16
[QUOTE=siennalizard]Let me know if you have any difficulties with this, or if I missed an obviously helpful source (or if this was actually helpful, not that I have ego problems, or anything...).
J.[/QUOTE]
It's all pretty clear, but I cannot make it work.  Is there any place to look for diagnostics?  The CUPS Gnome tool (from the client) provides absolutely nothing in the way of feedback.

The printer on the sharing machine is working properly.  On a previous installation on my client, I've been able to print to it.  Since I've installed Breezy, however, printing from the client has not worked at all.

I can bring up the CUPS web interface from the client and see the printer on the server.

[edit] OK it works now, but the URI I had to use is different from yours:

[http://host:631/printes/queue-name](http://host:631/printes/queue-name)

Also, for reasons unknown the gnome-cups-manager had initialized the printer with all the queue paused.

---

### Post by siennalizard on 2006-03-16
[QUOTE=pointym5]It's all pretty clear, but I cannot make it work.  Is there any place to look for diagnostics?  The CUPS Gnome tool (from the client) provides absolutely nothing in the way of feedback.[/QUOTE]

I must agree that cups feedback is very limited for clients in general. The status message in the gnome manager tool does not automatically update: it is read only when the properties of the printer are opened. The only consolation, I suppose, is that, once a printer's set up, it just doesn't seem to go wrong (at least until the next upgrade/ip change/ink outage/ authentication problem, etc.)

J.

---

### Post by ORF1000 on 2006-03-18
I think I'm doing OK as far as getting the client to pass the print job to the server with the printer connected, but something seems to be going bad after that.  When I hit "print" from the client computer, everything looks like it goes through OK; no error messages or anything unusual in the "properties" dialog for the printer.  But nothing actually prints.  The cups error_log on the server has the following:

    Adding start banner page "none" to job 21.
    Adding end banner page "none" to job 21.
    Job 21 queued on 'Office_Jet' by 'nobody'.
    Started backend /usr/lib/cups/backend/usb (PID 9529) for job 21.

I get the same entries whether I try to print by smb or ipp.

Both the server and the client machine will print locally without difficulty if the printer is connected directly to them.  It's an Office Jet 4200 on USB.

Any ideas would be appreciated.

Dave

---


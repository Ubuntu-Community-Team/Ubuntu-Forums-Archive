---
title: "Which email program will......."
date: 2009-02-19
forum: General Help
---

### Post by jbuczek on 2009-02-19
I'm retired and living in the Philippines. My "broadband" connection is a 4 km WiFi link at 256K.  For what it is, it's surprisingly reliable except for email.

I have lots of trouble SENDING email.  I suppose that's because ISP's have gotten careful because of spam concerns.  It often takes me half a day to get messages out although I have no problems getting them in.  The error message always concerns the POP server either timing out, sending an unexpected response or whatever.  I set myself a timer and try every half hour or so.

In the bad old dialup days when everything was unreliable, all email programs had an option to send, or try to send, anything pending in the outbox during any scheduled check for new mail. This feature now seems to be gone from most programs.

Do any of the popular linux email programs offer such a feature either natively or as an add-on?  

Otherwise I'm perfectly happy with Firefox.

---

### Post by howefield on 2009-02-19
> **jbuczek said:**
> The error message always concerns the POP server either timing out, sending an unexpected response or whatever.

POP deals with incoming mail. 

What program are you currently using for email and who is your email provider ?

---

### Post by ellgor on 2009-02-20
Hi,

Take a look at Kmail/Kontact, it has the requested features plus a lot more besides.

Regards, Ellgor.

---

### Post by razy60 on 2009-02-20
Couldn't you use a online email account such as hotmail, if you needed to save the message then you could save it to any document folder.

Raz

---

### Post by oldos2er on 2009-02-20
howefield is right; use SMTP to send email, not POP.

---

### Post by dcstar on 2009-02-20
> **oldos2er said:**
> howefield is right; use SMTP to send email, not POP.

It is not a choice, SMTP **only** sends e-mail & POP **only** receives it.

A POP timeout means the connection or the server has timed out when trying to check and/or receive incoming e-mail - possibly because of an unreliable connection.

If you have unreliable network comms you can increase the default timeout values for the particular mail programs you are using, but apart from that it is up to the network link and remote server.

---

### Post by dcstar on 2009-02-20
> **jbuczek said:**
> 
.........
In the bad old dialup days when everything was unreliable, all email programs had an option to send, or try to send, anything pending in the outbox during any scheduled check for new mail. This feature now seems to be gone from most programs.

Do any of the popular linux email programs offer such a feature either natively or as an add-on?  


Evolution (and I expect all other e-mail clients) will always try to send e-mails whenever they can, and they will remain in the outbox queue until sent.

---

### Post by demosthenese on 2009-02-20
> **dcstar said:**
> It is not a choice, SMTP **only** sends e-mail & POP **only** receives it.


Just as a point of information, you can run an smtp daemon to receive mail too.

---

### Post by knuthf on 2009-02-21
ok rookies,
POP is a telnet type of protocol - one byte at a time, while
SMTP is a RCP (remote file copy) type of protocol - one block at the time.

The failure on SMTP is related to packets being broken because your connection is reset. I wonder if the best and simplest remedy is to place a router on the link, so that the packets are not broken by sockets disconnecting due to timeout at transmission errors and resets.

Evidence that this will work can be obtained if you have a problem uploading files to your Gmail/Hotmail accounts - since you refer to Firefox that works fine. If smaller files goes fast, while a file of say 1MB is very difficult to attach - the reason is that the link connection is reset.

The router will hold your socket alive, even if this is disconnected and reconnected. It can be configured, but comes usually with software that manages the socket options better than I can describe for you. If you use a router - try another one and see if it improves things ;)

My Evolution is made so that it will work with a dial-up connection, and can be set to dial-up every now and then to send and check for mail - and use it on my laptop.:)

To the eager reader: Study TCP/IP options in "Sockets()" - here "SO_DONTLINGER" and "SO_KEEPALIVE". The problem is to detect a real "disconnect" immediately (which MS Windows cannot) or leave the connection "open" (which MS code will) - allowing others to "Connect()" to it. Ignorance of these features has introduced the need to extended ICMP to enable DHCP - so you can disconnect your laptop and take it home, and reconnect next morning resuming everything. If your were transmitting credit card transactions, these would also be open for others to resume - just by reading your IP and MAC address in the socket - and resume as you. See the issue? still banks use MS code, and are very surprised that their systems are compromised. On Linux your error message is "TCP OUTAGE" or "No more file descriptors available"......

---

### Post by jbuczek on 2009-02-22
OK! Some clarification.

Of course SMTP is the outgoing protocol, I mis-wrote.

I have both WinXP with Firefox 3.x and Ubuntu 8.10 with Firefox 3.x.  The problem exists with both.

My email providor is GoDaddy........ actually their server is "smtpout.secureserver.net".

The error message is usually something about "time out" but about 20% of the time it's "server refused connection" or "server returned unexpected reply".  The exact wording may be off a bit here.

I have a wierd setup.  The ISP uses the 192.168.x.x address group throught out it's network until it hits it's backbone portal so my transmissions are being handled by my router, then their Senao AP, then another AP that acts as a relay, then their headquarters AP then their master router then the portal.  I don't think any router I could get could do more than all this hardware is doing to keep the transmission alive.  

I think the route is just too slow. Traceroute shows the routing going through Manila, Taiwan, and four stations in Japan before it gets to the US. There is no variation in this routing.  About 1/3 of the time it's hung between Manila and Taiwan...... not surprising since PLDT (Philippine Long Distance Telephone) which owns the link is notorious about accepting massive overloads before upgrading anything.  Some times it hangs on the first link after leaving Japan, which I assume is the overhead or undersea link. Most of the time it makes it all the way to smtpout.secureserver.net but is rejected.

Supposedly an Australian outfit is laying a cable for a major new backbone from there to the Philippines.  Hopefully many of our problems will vanish when and if that happens.  May not.  It is said (have to be careful because libel is a felony here) that the last time China tried to run some new data links to here that the husband of the president demanded a bribe of $150M to permit it....... but that's getting off topic.  Just a glimpse of third world broadband problems.

So my only solution seems to be a program that will automate the multiple tries for me.  Since Evolution comes with Ubuntu.... I'll try that first then look at Kmail if Evolution is not satisfactory.

Thanks again.

---


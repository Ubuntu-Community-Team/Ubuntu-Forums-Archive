---
title: "Pidgin connections refused"
date: 2008-12-09
forum: General Help
---

### Post by randName on 2008-12-09
I have been using Pidgin for weeks with no trouble. For the past few sessions I have been getting "Could not establish a connection with the server: Connection Refused" for almost every account I have (Yahoo, Gmail and IRC)

It would appear that I can still use Meebo to access my accounts, and Rizon's Java Client still works for me. I tried different ports for each connection but to no avail.

I am not behind any proxy. My other internet applications (Liferea, uTorrent on Wine) still work normally. This seems very perplexing...

---

### Post by nishantman on 2008-12-09
I've had the same problem since updating today.  I have been using pidgin with no problems for many years.

---

### Post by randName on 2008-12-10
I don't really think the problem is with the updates...

For IRC the error is "Couldn't connect to host", but on Chatzilla its "Connection Refused"

And the online clients are still working fine...

---

### Post by cmonopoly72 on 2008-12-10
I can connect to GMail and to IRC. With AIM and Yahoo I get a "connection refused" message. I've noticed this happening for the last 2 days.

---

### Post by geodescent on 2009-04-19
**The skinny:** Flush your DNS cache.

[**_This particular Pidgin support ticket_**]("http://developer.pidgin.im/ticket/8853") addresses the issue for Windows users. I am not familiar with the command you'd use in Ubuntu but I wanted to try and help.

---

### Post by mr_bijae on 2009-06-24
I have been experiencing the same problem. When it first started I was getting the message "Connecting" but it never would connect and load my contacts. I found a thread that suggested to change the scs.msg.yahoo.com  to an IP address. I did this and it worked great for three days. Yahoo However seems to have blocked that ability because it's not giving the message, "connection refused" like the rest are experiencing. Here' the Yahoo Help post on the subject

[http://answers.yahoo.com/question/index?qid=20090617171643AA8LFyw](http://answers.yahoo.com/question/index?qid=20090617171643AA8LFyw)

I can connect with KOPETE without fail! Guess it's just time to dump pidgin and go with Kopete, even though it too has some bugs.. 

<shrug>

---

### Post by amarendra on 2009-08-13
while trying to connect to IRC.freenode, following error is displayed : "Couldn't connect to host"

I am behind a linksys router. no proxy. in fact same Pidgin connects to my gmail a/c just fine.
i am using it on windows.

PS. i understand this is not the best place to ask win Qs but I am stuck with my 9.04 for last 3 months.

---

### Post by Katalog on 2009-08-13
[saracsm]It's a conspiracy to get everyone to switch to Empathy.[/sarcasm]

---

### Post by andrew.46 on 2009-08-13
Hi amarendra,

> **amarendra said:**
> while trying to connect to IRC.freenode, following error is displayed : "Couldn't connect to host"

This message is not uncommon on my own setup when attempting to connect to Freenode (with irssi) but usually an immediate attempt to reconnect is successful. I will have to admit that when this happens I have simply put it down to the vagaries of the network rather than a flaw in my own setup.

Andrew

---


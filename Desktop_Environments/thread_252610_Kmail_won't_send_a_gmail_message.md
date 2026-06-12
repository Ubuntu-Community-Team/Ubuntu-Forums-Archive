---
title: "Kmail won't send a gmail message"
date: 2006-09-07
forum: Desktop Environments
---

### Post by dyoung66 on 2006-09-07
kmail won't send a gmail message.
 
Ive tried the following and some variations of the below settings to get kmail to work.
 
 From google:
 
 Outgoing Mail (SMTP) Server - requires TLS: smtp.gmail.com (use authentication)
 Use Authentication: Yes
 Use STARTTLS: Yes (some clients call this SSL)
 Port: 465 or 587
 
 I tried these and other settings and everytime I get the error " Unrecognized transport protocol - Unable to send message"
 
 POP works fine, I deleted the smtp settings and set it up again but still get the same error.
 
 Does anyone else have this problem??

---

### Post by dyoung66 on 2006-09-08
<bump>

Can anyone send a message through gmail using kmail ?
Even a yes or no answer would be helpful so I know whether its me or them that is the problem.
Cheers.

---

### Post by Junx on 2006-09-09
I use KMail + Gmail, so here's my settings:

Username: [email]foo@gmail.com[/email] (need the whole email address)
Server: smtp.gmail.com
Port: 25 (amazing, I know, I thought you needed to use something else with them, but I guess not)
Encryption: TLS
Authentication Method: Plain

---

### Post by dyoung66 on 2006-09-09
Hi Junx, 
thanks for the reply, I tried those settings and I still get 
" Unrecognized transport protocol - Unable to send message".

Hmmm, I'm dumbfounded.

---

### Post by wouterd on 2006-09-09
I use KMail and Gmail:

[general]
host: smtp.gmail.com
port: 465
<server requires authentication>
login: user (no .gmail.com!)
password ****

[security]
<ssl>
<plain>

good luck!

---

### Post by dyoung66 on 2006-09-24
Problem Solved.
My ISP was blocking all SMTP mail that wasnt using their own server.
So I entered their SMTP server info instead of gmails and wham bam thankyou mam, it works fine.
Hurrah. Thanks to wouterd and junx for helping out.

---

### Post by MartynasP on 2008-01-23
> **dyoung66 said:**
> Hi Junx, 
thanks for the reply, I tried those settings and I still get 
" Unrecognized transport protocol - Unable to send message".

Hmmm, I'm dumbfounded.

The problem is not in Your ISP or settings, I think. The real problem is in Your FIREWALL. I'm using Kubuntu, KMail and Guarddog firewall and had the same problem. If You are using Guarddog, You have to create a custom protocol.

Start Guarddog, Advanced tab, in User Defined Protocols click on New Protocol, write the name You want, choose type TCP, ports 465-465. (In my Bidirectional checkbox is cross and I can't change it). Then click on Protocol tab, choose Defined Network Zone - Internet, in Zone Properties tree open User Defined folder, there should be Your protocol, just created. Click on it checkbox, that this protocol would be permitted. Then click Apply button, Your firewall will be restarted. Click OK and exit Guarddog with OK button.

If the problem still exists, check KMail settings: Settings, Configure Kmail, Accounts, Sending, choose Your Gmail outgoing account:
[LIST]
[*]Name - Your email address
[*]Host - smtp.gmail.com
[*]Port - 465
[*]Server requires authentication
[*]Login - Your email address
[*]Pass - Your email password
[*]Store SMTP pass
[/LIST]

In Security tab:
[LIST]
[*]Encryption - SSL
[*]Authentication method - PLAIN
[/LIST]

If the problem persists, read the Guarddog documentation:
[http://www.simonzone.com/software/guarddog/manual2/index.html](http://www.simonzone.com/software/guarddog/manual2/index.html)

Good luck! :)

---


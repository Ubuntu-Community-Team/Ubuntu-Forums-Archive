---
title: "Cannot send email via smtp"
date: 2009-03-09
forum: General Help
---

### Post by gustavocqd on 2009-03-09
Hi,

I had never seen this problem before and googling it has not pointed me in the right direction yet. Hope you can give me some hints. I cannot send emails via smtp. I've tried configuring evolution and thunderbird with identical results, they complain that the connection cannot be established. However doing

```
telent smtp.server 25
```

works fine.

In addition I can also send emails from other windows boxes at work (mine is the only linux).

I have iptables disabled and the smtp server does not require authentication.

Any clues? Thanks in advance

---

### Post by jonobr on 2009-03-09
HEllo


I would recommend continuing the SMTP commands to see if something stops you at some point.

after you open the SMTP connection , try executing the following

```

telnet <smtpserver> 25

```
Usually indicates connection is open and ready

```

helo mailserver.com
```
Usually responds with a 'pleased to meet you" or ready or similar....

```
mail from:me@here.com
```
identifies who you are

```
rcpt to:you@there.com
```
Identifies recipient and usually tells you to enter data.

See how far you get with that and if any errors occur

---

### Post by gustavocqd on 2009-03-10
Thanks jonobr,

I followed the those steps and everything seems fine. I can even send mails from madeup users (I guess this is what spamers do). However I still can't send mail from thunderbird or evolution.

---

### Post by gustavocqd on 2009-03-10
By the way, I just realised tha this is rather serious, because if I can do this it means that anybody can, since this smtp server doesn't ask for user authentication. I will report this issue to my ISP.

Also It made me think. Is there anything set in ubuntu that prevents connection to this unsecure smtp servers?

---

### Post by jonobr on 2009-03-10
Hello


I recommend using wireshark or tcpdump to see whats going on at a packet level.
You should be able to see what packets are being issued and if they are getting to the SMTP server.

It is odd that the firewall being disabled it works on cli but not the application.
My original thought was your ISP was blocking SMTP, which is not unusual,
however, your test disproves that.

---

### Post by gustavocqd on 2009-03-10
Oddly enough if I try a different smtp server (my old uni one of in which I still have an account), which requires athentication everything runs fine.

I tried running tcpdump, but I can't really intepret the results.

sudo tcpdump dst smtp.server
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
17:01:41.570188 IP local.42393 > mail.smtp: F 0:0(0) ack 1 win 92 <nop,nop,timestamp 136236867 1268501434>
17:01:41.583749 IP local.42393 > mail.smtp: R 2345604383:2345604383(0) win 0
5 packets captured
7 packets received by filter
0 packets dropped by kernel

The "7 packets received by filter" makes me think that is fine...

---

### Post by hub_cap on 2009-03-10
I was having trouble with Evolution sending mail to the comcast server because comcast requires a different port than the default.

I simply configured the smtp server as smtp.comcast.net:**587** and my problem was solved. Perhaps this can help you. Check what your outgoing mail server requires.

---

### Post by gustavocqd on 2009-03-10
Hello hub_cap.

Thanks for your suggestion. The fact that I can connect to the server through the port 25 proves that what you suggest is not the issue here (it worked for you because your smtp server probably requires a secure conection tsl or ssl). 

But I had to admit that I'm puzzled with this.

---

### Post by Rallg on 2009-03-10
Gmail works fine for me, using Thunderbird on Ubuntu 8.10, i386. I notice that the smtp configuration (see Google's instructions for Gmail) uses a port other than the default, and use a protocol other than the default.

If you dual-boot, does your mail work for you on the same computer, using Thunderbird on Windows?

My private (not Gmail) E-mail service does not allow me to send mail via Thunderbird, either on Ubuntu or Windows, unless I choose a particular port that is not the default. But I can read the E-mail.

---

### Post by jonobr on 2009-03-10
gustavocqd, are you using gmail?
If so the gmail smtp server uses tls and a different port number to port 25.
You can however, connect on port 25, but it doesnt use that for integration with thunderbird etc....

see [THIS]("http://http://mail.google.com/support/bin/answer.py?answer=13285") for info

However, in the thread I notice there is no mention of using gmail.
IF you are, you need to change your port number.


Also, the weakness you mention about lack of security is a "known" thing.
I used to do training and for demo purposes I would show using SMTP and spoofing the email address of someone in the group in front of me.
They introduced ESMTP, TLS etc to get away from that, however, you can see why spamming happens.

---

### Post by gustavocqd on 2009-03-12
No, I'm not using gmail, but mail.xs4all.nl (which is our ISP in the office). I do not have dual boot, however I have access to two computers in the office (Windows and Ubuntu) with the same mail configuration thunderbird works in Windows and doesn't in Ubuntu. This is way I know is not a port issue. I'm more incling to a Windows/Linux configuration difference. It might me something else but I'm clueless as of what...

---

### Post by ssivil on 2009-03-12
About 2 days ago, Thunderbird was no longer able to send mail via smtp.  I can receive, but not send.

Thunderbird has been working fine since I installed it when 8.10 was released.  I called my ISP and they tell me there is a problem with Thunderbird, and suggested I use Evolution instead.  They didn't mention what the problem was, but simply said they are "tightening security".

I installed Evolution and it works perfectly.  I'd like to return to Thunderbird, but wonder if Evolution is really more secure than Thunderbird as they state.

The outgoing mail server as defined in both Thunderbird and Evolution is
: smtp.mail.wideopenwest.com

I tried dozens of different ports in Thunderbird (as suggested on the Mozilla help site), but none worked.  I don't see where ports are defined in Evolution so not sure which they use.  This led me to call my isp again.  They said all ports have remained the same and reiterated the Thunderbird security issue.

Any information is truly appreciated!

---


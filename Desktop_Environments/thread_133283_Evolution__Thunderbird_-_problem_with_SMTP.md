---
title: "Evolution / Thunderbird - problem with SMTP"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Morbett on 2006-02-19
I am able to receive mail through both programs, but not send mail.  My smtp information is entered correctly, because I used to be able to send mail and, without any significant changes to the preferences, it just stopped working. 

Since it affects both Evolution and Thunderbird, I figure it is not a bug with the application itself but possibly a system setting.  Any ideas?  Thanks.

---

### Post by amoser on 2006-02-19
It sounds like a problem with the STMP server.  If it effects both Evolution and Thunderbird then it has to be with the server.  Evolution and Thunderbird do not use the same system settings, they are independent of each other.  Wait about a day or so, and see if it works then.

~Alan

---

### Post by Morbett on 2006-02-20
Thanks for the reply.  It's been like this for a few days, so I don't think that it's the particular SMTP server.  

I have a feeling that it's something in my system files.

I did change my ISP recently.  Could a new ISP somehow affect sending mail through SMTP ?

---

### Post by kaamos on 2006-02-20
Yes it would, since normally (at least around here) the smtp server is provided by the isp. Find out what smtp server you new isp uses, and change to that.

---

### Post by Morbett on 2006-02-20
But my internet provider is not affiliated with my email address.  Not the same company...

---

### Post by Digidiz on 2006-02-20
i know this may sound silly, but have you selected SSL port 995??

---

### Post by Morbett on 2006-02-20
Hello.  Thank you.  I tried that, but still had no luck.

---

### Post by jaywatkins on 2006-02-20
Do you have to authenticate to your SMTP server?  If so, do you have to use an alternate port?  547???

/J

---

### Post by jaywatkins on 2006-02-20
Do you have to authenticate to your SMTP server?  If so, do you have to use an alternate port?  547???

/J

---

### Post by Morbett on 2006-02-21
[QUOTE=jaywatkins]Do you have to authenticate to your SMTP server?  If so, do you have to use an alternate port?  547???

/J[/QUOTE]

No, my SMTP server does not have to be authenticated.

---

### Post by Digidiz on 2006-02-21
is it gmail or yahoo or something else??

---

### Post by dcstar on 2006-02-21
[QUOTE=Morbett]No, my SMTP server does not have to be authenticated.[/QUOTE]
In a terminal, do:

telnet smtp.server.whatever.com 25

and see what you get.

---

### Post by Morbett on 2006-02-21
It tried the address, but the connection timed out.  

On a side note, I am able to use the company's webmail service through browser.

---

### Post by dcstar on 2006-02-22
[QUOTE=Morbett]It tried the address, but the connection timed out.  

On a side note, I am able to use the company's webmail service through browser.[/QUOTE]
Webmail is **NOT** SMTP, if SMTP connections time out, then there is probably a firewall specifically blocking SMTP connections.

Ask your IT department when they started blocking outgoing SMTP connections.

---

### Post by sanchrts on 2006-07-03
David

I have been lurking in this thread because I seem to have the same problem with SMTP servers on Thunderbird and Dapper Drake.

I installed Thunderbird from Synaptic Package Manager and whilst all aspects of my PC's (Dell Latitude X300) connectivity work fine (local SMB network browsing, gaim, web browsing, POP) I just cannot seem to get SMTP to work.

My SMTP is authenticated and I use a password via SSL on port 2525 (since I send a lot of email from my laptop from public hot-spots I am concerned about password sniffing over open networks) and as with Morbett my telnet attempt to connect to the SMTP server also timed out.

Thanks in advance for any light you can shed.

regards
Rafael

---


---
title: "Hotway"
date: 2005-12-11
forum: General Help
---

### Post by dizzy1234 on 2005-12-11
I've just installed a package called "Hotway" ([Deb package info](http://packages.debian.org/unstable/mail/hotway)) which claims to "acts like a pop3 server, but actually goes to an HTTPmail server to retrieve requested mail". Does anyone know how to set this up to work with the dreaded (sorry) hotmail?

---

### Post by frodon on 2005-12-12
Does what you want is to get your mails from your hotmail account on your computer ?
If yes i advice you [gotmail]("http://sourceforge.net/projects/gotmail"), it's a perl script which dowload the mails on the computer in a file, then after that all you have to do is to tell evolution, thunderbird , ... to look in this file for new mails.

---

### Post by GeneralZod on 2005-12-30
This is actually pretty easy, although the Ubuntu package seems to be missing a dependency (inetutils-inetd).

Install hotway from the repositories, then do

```

sudo apt-get install inetutils-inetd 
sudo /etc/init.d/inetutils-inetd restart

```

The hotway daemon should now be running on port 110 - to test it out, do

```

telnet 127.0.0.1 110

```

This should bring up the hotway server - type 

```

quit

```

and press enter (you may have to do this more than once).

Now you simply have to configure your e-mail client to get your e-mails via hotwayd.  How to do this depends on the client you are using, but generally you just have to enter "127.0.0.1" as the address for the POP3 server, and 110 as the port.

hotway is in my opinion a little better than gotmail as it requires less HTTP requests and will not break whenever Microsoft changes the layout of the hotmail.com page.

---

### Post by gltonn on 2006-01-21
I got Hotway installed and it works, based on you test and I even was able to recive email. Is there a way to configure Evolution and Hotway to send emails, through Hotmail?

---

### Post by adamonduty on 2006-01-21
You don't need to use hotmail to send emails from your hotmail account. Your existing SMTP server (the one from your isp) will most likely send emails from hotmail.com as well as from any other accounts.

---

### Post by gltonn on 2006-01-21
That worked great. It even puts in a drop down box to select the mail service I want to send the email from!

Thanks

---

### Post by Mitush on 2006-02-21
Hotway + evolution combo worked for me too. Just wanted to mention two things for people trying to set it up. First, indicate your full email (e.g. [email]blah@hotmail.com[/email]) as a username. Second, you don't have to specify port (110) anywhere in the setup, it works anyway.

---

### Post by Mitush on 2006-02-23
Using hotway and evolution, when I delete/expunge messages in evolution they are **NOT **deleted on the hotmail.com. I regularly have to go to hotmail.com with a browser and delete the messages which I've already deleted in evolution! Any suggestions on how to fix this?

[I do have "expunge trash folder on exit" turned on in evolution settings. ]

---

### Post by cantormath on 2006-03-23
Does anyone know why using evolution or thunderbird, and hotway, the only file imported is inbox and not the sent, junk, drafts etc.........
this is a deal breaker for me. 

the expunge is working fine though.....

---

### Post by hiptrop on 2006-03-30
mhmhm i have things set up now ... well as far as my knowledge goes :P 

i can recieve all emails now ... but i cannot send any ... 
does anybody know what settings i have wrong ? the setup for smtp server is : 127.0.0.1     :.. unfortunalty this won´t work :( 

any help would be nice :) thanks !!

---

### Post by hiptrop on 2006-03-30
nervermind :) needed to install hotsmtp and configure it :) 

works now :)

if anybody needs help check out this page ( spanish but with babelfish no problem !!)

[http://soleup.eup.uva.es/mario/post/1/194](http://soleup.eup.uva.es/mario/post/1/194)

---

### Post by Mikebgr on 2006-05-03
first of all zod thanks for the info. But I still can't get the daym thing to work. 

What I have done:

- First I downloaded and compiled hotwayd (is it different from hotway?). It had some dependencys, so I had to install some other packs first. Some of them where cyrus mail packs and their dependencies.

- One of the packs made me do some post-install configuration but I dont remember which one. Some of the configurations were about localhost etc

- I apt-got the hotway package

- When I  ```
telnet 127.0.0.1 110 : 
```
I get:
```
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
```

- Thunderbird when asked to connect to localhost and check mail, just stands there trying to connect and timeouts after some time.

Any ideas?




Edit: these are the packages that I installed to install hotwayd:

```
cyrus-admin (1.5.19-20)
cyrus-dev (1.5.19-20)
cyrus21-clients (2.1.18-1ubuntu1)
cyrus21-common (2.1.18-1ubuntu1)
cyrus21-doc (2.1.18-1ubuntu1)
cyrus21-pop3d (2.1.18-1ubuntu1)
cyrus2courier (1.3-2)
gawk (1:3.1.4-2)
libcyrus-imap-perl21 (2.1.18-1ubuntu1)
libhesiod0 (3.0.2-15.1)
libsasl2-dev (2.1.19-1.5ubuntu4.2)
libsnmp4.2 (4.2.5-5ubuntu0.1)
libzephyr3 (2.1.20010518.SNAPSHOT-12)
postfix (2.2.4-1ubuntu2)
tcl8.3 (8.3.5-4)
```

---

### Post by dresnu on 2006-05-25
Following GeneralZod's instructions I got hotwayd running and setup Kmail but when I try to download mails I get this message: "Hotmail said you must pay money to have WebDAV access".
Microsoft is mocking me...

---

### Post by hype on 2006-06-11
dresnu: same message here :s

---

### Post by sushi on a grill on 2006-06-13
edit: never mind, i think i got it going

---

### Post by writeandrevise on 2006-06-16
First day with linux.  I downloaded the zip of gotmail.  I know how to unzip with windows, how do I get this installed now?

---

### Post by DavidTangye on 2006-06-26
[QUOTE=cantormath]Does anyone know why using evolution or thunderbird, and hotway, the only file imported is inbox and not the sent, junk, drafts etc.........
this is a deal breaker for me. 

the expunge is working fine though.....[/QUOTE]
You did not read the man or README did you :-).

You need to explitely tell hotway each folder you want brought down, if not the inbox.

---

### Post by DavidTangye on 2006-06-26
You did not read the man or README did you :-).

Invoke hotwayd -r

---

### Post by jonasan on 2006-11-06
> **dresnu said:**
> Following GeneralZod's instructions I got hotwayd running and setup Kmail but when I try to download mails I get this message: "Hotmail said you must pay money to have WebDAV access".
Microsoft is mocking me...

> **hype said:**
> dresnu: same message here :s

Microsoft appear to be mocking everybody! Even there own Outlook users, although Microsoft have been oh so gracious to wait till next year before they start charging for the 'privilege' of using there bloated service.

Is there a work around for the non-outlook users amongst us?

---

### Post by gatti on 2006-11-06
> **gltonn said:**
> I got Hotway installed and it works, based on you test and I even was able to recive email. Is there a way to configure Evolution and Hotway to send emails, through Hotmail?
you need hotwaysmtpd to send from web based e-mail, certainly works well with lycos mail and is a neater solution than using the ISP mail service to send and web based to receive

---


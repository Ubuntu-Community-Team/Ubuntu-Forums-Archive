---
title: "Mail - Command Prompt - Easy - SMTP"
date: 2009-04-14
forum: General Help
---

### Post by gbxfan on 2009-04-14
Hello,

Well I am dizzy looking through Google and trying to figure out what I should use for command prompt email (outgoing only - don't need incoming) that will be used by shell script to email the results.

Can somebody point me in the right direction of an app they're  using that utilizes SMTP and is faily easy to configure and has commands I can use from a command prompt (shell script)? Help.

Thanks!

---

### Post by HermanAB on 2009-04-14
The simplest MTA for use with shell scripts or web server applications is nullmailer (provided that you already have a working mail server somewhere else, eg. your ISP mail server).  Some Googling will find it.  You only need to configure two things to get nullmailer to work: Who are you and where to send the mail to.  It is almost trivial to install - well, totally trivial compared to anything else.

If you need a full featured mail server, try Citadel - it installs in about 20 minutes using the Easy Install script and it 'Just Works', provided that your network and DNS are configured properly.

---

### Post by gbxfan on 2009-04-14
Thank you! Since I am new to setting this up, let me tell you I can use the Evolution program I received with Ubuntu 8.10 client and by putting in just the SMTP address in the configuration was able to send a message to myself with the GUI. Can't seem to figure out how to do that with the command prompt or I would be all set. Knowing this, do I need any other software parts or does it seem just an MTA (is that also known as just a mail client?)?Thanks for your patience and help.

---


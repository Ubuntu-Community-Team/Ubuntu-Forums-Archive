---
title: "Need a bit of help, Freepops and Evolution mail"
date: 2006-01-18
forum: General Help
---

### Post by Yoshimitsu8 on 2006-01-18
Hey all,
I have looked this over [http://ubuntuforums.org/showthread.php?t=36002](http://ubuntuforums.org/showthread.php?t=36002) but it seems to be a bit old. They now how freepops in synaptec which I downloaded. I got port 2000 open and it looks like it should work, however every time I try to get my mail it gives me

Error while Fetching Mail.
Unable to connect to POP server localhost.
Error sending password: Operation now in progress

So far I have hotway working currently with evolution (using port 110) and now I tried to add freepops for my yahoo account. 
My current configuration for yahoo account is:
Receiving: localhost:2000
Sending: outgoing.verizon.net:8025

I know the outgoing/sending is fine because it is what I use for my hotway, however the locathost one isn't work.
Any sugguestions on how to make it work?
Thanks

---

### Post by makadam on 2006-10-26
Hello

I resolved my problem by installing the freepops init script using this command:
```
sudo update-rc.d freepops default
```

---

### Post by sidcypher on 2007-12-12
so, since i just got this far, free pops never worked for me. 

and just noticed that it doesn't have smtp like yahoopops does....

any suggestions getting something that will do both? maybe yahoopops?

Thx
Cypher

---

### Post by rlcompton on 2008-04-01
I am using Evolution & Freepops (from apt-get) with Gutsy to get Yahoo mail. I have a router & I use pops with 127.0.0.1:2000 (localhost:2000 also works) as the server name plus the port. I put Freepopsd in the Sessions (startup). Since Gmail is my smtp server I don't know if this works with Yahoo as the smtp server.
R Compton :)

---

### Post by Seisen on 2008-04-01
Check this out [http://www.geocities.com/t_skariah/ypops/]("http://www.geocities.com/t_skariah/ypops/") this is how I used to access yahoo mail from Ubuntu.

---


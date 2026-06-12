---
title: "postfix problem, sasauthd not found"
date: 2008-12-28
forum: General Help
---

### Post by hxvb on 2008-12-28
Hi, 
for testing purpose(school project), i have to install an smtp server on my laptop, first of all do I need an ubuntu server or any version is ok?
because i have ubunto 8.4 installed, and for the smtp server i work with postfix, but never succeed to get it working. after many internet search (lots of postfix manual) I'm not able to execute : 
/etc/init.d/saslauthd start 
saslauthd was not found under init.d
I'm a ubunto beginner, any help is welcome.
if some one have an idea or a good manual please help me, thanks.

---

### Post by HereInOz on 2008-12-29
Check out this link.  You will need to start from scratch if you follow this tutorial, but it will all work.  

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

There will be no desktop after this install, it will be command line only, so to get a gnome desktop, you will need to run (I hope I am right here):

sudo apt-get install ubuntu-desktop 

Good luck.

---

### Post by dcstar on 2008-12-29
> **hxvb said:**
> Hi, 
for testing purpose(school project), i have to install an smtp server on my laptop, first of all do I need an ubuntu server or any version is ok?
because i have ubunto 8.4 installed, and for the smtp server i work with postfix, but never succeed to get it working. after many internet search (lots of postfix manual) I'm not able to execute : 
/etc/init.d/saslauthd start 
saslauthd was not found under init.d


Why do you think you need to run that command?, postfix does not need it as it uses libraries it installs.

---

### Post by hxvb on 2008-12-29
> **HereInOz said:**
> Check out this link.  You will need to start from scratch if you follow this tutorial, but it will all work.  

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

There will be no desktop after this install, it will be command line only, so to get a gnome desktop, you will need to run (I hope I am right here):

sudo apt-get install ubuntu-desktop 

Good luck.

thanks, I'm downloading the iso to try it.

> **dcstar said:**
> Why do you think you need to run that command?, postfix does not need it as it uses libraries it installs.
well I don't know me either, I just followed the manual :D. other thing, when I enter :
telnet localhost 25 
i get : connected to 127.0.0.0
and a message like this : '^]' to quite 
then I can enter text.

---

### Post by hxvb on 2008-12-29
it's working, thank you. I didn't install ubuntu server, I'm not sure how but after system updating I was able to install sasl2.bin package then I simply reinstall postfix and configure it, and thats it. thank you again ^^.

---


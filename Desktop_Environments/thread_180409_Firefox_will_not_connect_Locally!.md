---
title: "Firefox will not connect Locally!"
date: 2006-05-22
forum: Desktop Environments
---

### Post by rnfuller on 2006-05-22
I posted this on the Kubuntu forum but it really is not a problem specific to KDE.

I have a weird problem going on I can't seem to figure out. I just did a fresh install of Dapper Kubuntu on my laptop. I have a Breezy system setup on my network as a server that runs Apache that I use for a Intranet Server and for development. When I try to go to my local webpage on my laptop, It fails to connect. I can't get to Webmin on the server either. But if I try the same thing using Konqueror instead of Firefox, it works fine!

I have no proxy settings in Firefox and I can access Internet sites fine. I am at a loss as to what is going on. Anybody have any suggestions?

I can go to [www.google.com](www.google.com) or any other internet site fine with firefox, but if I type [http://192.0.168.3](http://192.0.168.3) to go to my breezy server, I get the message Failed to Connect to Web Server.  If I use Konqueror to do the same everything is fine.  I get to my Intranet site.  The same thing happens when I got to Webmin with [https://192.0.168.3/10000](https://192.0.168.3/10000), Firefox chokes, Konqueror connects fine.

I tried sudo apt-get remove firefox, and then sudo apt-get install firefox with no change.

I hate Konqueror as a web browser.  What in the world is wrong?

Thanks
Randy

[B]
SOLVED!
Remove all mozilla stuff with Adept and then re-installed.  Apt-get remove and install just did firefox and left other stuff behind.[/B]

---

### Post by zluka on 2006-05-22
i'll take a guess here.. did you check your connection settings of firefox? or maybe you have a problem with your firefox extentions? if konqueror connects and firefox does not, packet loss or firewall-blocking is out of the question (logic says so :-k )

what did you change in your firefox after install?

---

### Post by rnfuller on 2006-05-22
The only thing I remember changing after install, was the proxy settings.  I was having wireless issues after install, and was trying a lot of stuff to get my wireless problems solved.  I finally solved wireless by blacklisting the bcm43xx drivers and using ndiswrapper, and that is when I noticed I could no longer get on my intranet with firefox.

I do not have any proxy settings in firefox now.

Randy

---

### Post by rnfuller on 2006-05-22
Any Ideas?

---

### Post by zluka on 2006-05-23
did you change something in the "about:config" page? that sux sometimes.

or try "complete removal" of firefox from synaptic, which also deletes the conf. files, and install again. sometimes helps..

if there's something i hate about linux, that's it.. problems come and go, but while you're fighting to solve one, you can break something else, sometimes forever.. maybe that's because i'm not an expert (yet ;) ), anyhow no good.

hope this helps

---

### Post by rnfuller on 2006-05-23
zluka, you hit the nail on the head.  I had tried to uninstall and reinstall several times with apt-get, but until I went to Adept and searched for mozilla and remove everything with mozilla in the name, and then reinstalled.  After that it worked fine.

I not an expert yet either, but you're right, it is easy to break something, but thank goodness, you usually can fix it without a complete re-install of the OS like Windoze!

Randy

---

### Post by zluka on 2006-05-24
thanx man, you're the first guy i was able to help (yet ;) )

i'm not defending winblows, don't get me wrong.. i've written in the testimonials section, i'm sick and tired of boot-up freezes, microsoft bulletins and such (which don't do sh.. actually) and such..

and i really don't remember the days i worked on dos 3.11, maybe i was even worse, practically without any experience on pc, then found out about config.sys, himem.sys and else, was happy as i had found gold ;)

it's just getting used to. and i'm just older, busier and the world is dirtier..

anyhow i'm not leaving linux. especially ubuntu.

ps: i was interested in computers in the first place because i wanted to learn how it "ticked" inside. and linux gives much more chance to learn this than m$

---


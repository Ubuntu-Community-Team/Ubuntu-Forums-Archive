---
title: "Ubuntu Virus ?"
date: 2009-04-25
forum: General Help
---

### Post by toontastic on 2009-04-25
Ok I know Ubuntu shouldn't get viruses but I'm a little concerned with my copy. 

I have upgraded to Ubuntu 9.04 yesterday. Since then whenever I go to google or any other search engine for that matter I get a problem where the correct webpage does not load. It's not constant but it does happen every few searches on google or yahoo or most other search engines I've tried. 

So say for example I type ubuntu in the search, I'll get all the usual ubuntu search results however when I click on the link it takes me to in googles case myspace however thats via click.mygeek.com and [www.fasttools.biz](www.fasttools.biz) which appear very dodgy. When I say it goes via those two, they appear in the bottom left as the myspace page loads. The final page I end up at is [http://uk.myspace.com/?utm_source=Adon&utm_medium=cpc&utm_term=gen2&utm_content=gen&utm_campaign=mrc](http://uk.myspace.com/?utm_source=Adon&utm_medium=cpc&utm_term=gen2&utm_content=gen&utm_campaign=mrc)

on yahoo it's different it ends up at [http://people--search--engine.com/](http://people--search--engine.com/) after going via finefinder.net and [www.mirago.net](www.mirago.net). Unlike google the end result for yahoo is not always the same.

When I click on a link it takes ages to load. Sometimes I will actually get to the site I want but very rarely.

Please please help basically I can't use search engines any more.

---

### Post by ddrichardson on 2009-04-25
Can you post /etc/hosts and can you run Firefox from the terminal using```
firefox -P
```This allows you to change profiles - try a new one and see if it still occurs.

---

### Post by toontastic on 2009-04-25
> **ddrichardson said:**
> Can you post /etc/hosts and can you run Firefox from the terminal using```
firefox -P
```This allows you to change profiles - try a new one and see if it still occurs.

127.0.0.1	localhost
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Thanks.

---

### Post by toontastic on 2009-04-25
> **ddrichardson said:**
> Can you post /etc/hosts and can you run Firefox from the terminal using```
firefox -P
```This allows you to change profiles - try a new one and see if it still occurs.

I've tried using Epiphany and get the same problem should I still do this ?

---

### Post by toontastic on 2009-04-25
I tried doing it anyway and it still happens, took a bit longer though.

---

### Post by ddrichardson on 2009-04-25
The hosts file is normal so if there's any kind of compromise it is unlikely to be system wide, re-directors normally aim for that file.

Have you got another account to test from? If not can you create one and try again - this'll help pinpoint the location of the fault.

---

### Post by calebk on 2009-04-25
That is really strange! I would suggest booting from a ubuntu live cd and see if it does that on there. If the problem is the same on the live cd then it is definitely not a virus. If the problem doesnt happen on the live cd then there is a problem with your installation and probably the best thing to do is back up important files and reinstall.

---

### Post by albinootje on 2009-04-25
> **toontastic said:**
> 
When I click on a link it takes ages to load. Sometimes I will actually get to the site I want but very rarely.


Can you please use an Ubuntu live cd (or usb stick) and test the same things ?
With that we can see whether your installed Ubuntu installation is affected or not.
If you get the same problems in the live session i can imagine it could be because of your adsl-modem/cable-modem and/or the DNS-servers you're using.

---

### Post by toontastic on 2009-04-25
I'll give a new account a go see what happens thanks

---

### Post by albinootje on 2009-04-25
> **calebk said:**
> If the problem doesnt happen on the live cd then there is a problem with your installation and probably the best thing to do is back up important files and reinstall.

Not just reinstall right away imho. If the Ubuntu installation is really affected by something, it could be useful to find out what exactly where the problem comes from.

---

### Post by toontastic on 2009-04-25
Not sure if it's releated but I've just this second got a Tracker Applet pop error it says:
Tracker
There was an error while performing indexing

Index Corrupt

Reindex all contents, Cancel, OK

No matter what I click the error won't go. 

I'll do the new account now.

---

### Post by ddrichardson on 2009-04-25
> **albinootje said:**
> Not just reinstall right away imho. If the Ubuntu installation is really affected by something, it could be useful to find out what exactly where the problem comes from.
Yes I agree and the reinstall reaction is usually more of an inconvenience to users than we realise when we suggest it.

---

### Post by toontastic on 2009-04-25
> **albinootje said:**
> Not just reinstall right away imho. If the Ubuntu installation is really affected by something, it could be useful to find out what exactly where the problem comes from.

How would you know that if I reinstalled ?

Sorry misread

---

### Post by toontastic on 2009-04-25
Minor issue with the live CD I have no CD/DVD drive on this laptop.

---

### Post by calebk on 2009-04-25
You are probably right,albinootje. I just thought that it would be the best thing to do as it seems such a strange problem.

Listen to albinootje, he is obviously the expert

---

### Post by calebk on 2009-04-25
Ok you will need to install it onto a usb stick, do you have one of those?

---

### Post by ddrichardson on 2009-04-25
Can you disable the tracker applet? Xkill will do it.

---

### Post by toontastic on 2009-04-25
I do but when I have tried previously the usb build has not worked so detailed instructions please :D

I've created a new user called test, exact same problem.

---

### Post by albinootje on 2009-04-25
> **toontastic said:**
> Minor issue with the live CD I have no CD/DVD drive on this laptop.

Use [http://unetbootin.sf.net](http://unetbootin.sf.net) to create a bootable usb stick to boot 
from.
You can prepare this on another Linux or MS-Windows computer.

---

### Post by toontastic on 2009-04-25
> **ddrichardson said:**
> Can you disable the tracker applet? Xkill will do it.

reboot seemed to stop that just wasn't sure if it was related.

---

### Post by toontastic on 2009-04-25
> **albinootje said:**
> Use [http://unetbootin.sf.net](http://unetbootin.sf.net) to create a bootable usb stick to boot 
from.
You can prepare this on another Linux or MS-Windows computer.
I'll give it a go, do you want me to do the same things when I'm booted on USB

---

### Post by albinootje on 2009-04-25
> **calebk said:**
>  Listen to albinootje, he is obviously the expert

Thanks for the compliment, but I'm not an expert. 
I'm just an average Linux sysadmin trying to use common sense ;-)

---

### Post by mbeach on 2009-04-25
are other machines on this same network?  do they exhibit the same behaviour?  Are you using some special dns servers?  If you have access to your DNS server, or router, try OpenDNS's dns server ips and see if you get the same behaviour.

opendns:
[https://www.opendns.com/start/](https://www.opendns.com/start/)

---

### Post by albinootje on 2009-04-25
Yes, try the same things in Firefox and Epiphany browser as you did 
before. 

It is possible that your DNS-servers are "hijacked".

Make sure you choose "Ubuntu" live (during the creation of the bootable usb stick with unetbootin), and not the netinstall option.

---

### Post by calebk on 2009-04-25
Yes, create usb unetbootin, if you can do it on a windows machine because the Linux version didn't work for me.

---

### Post by toontastic on 2009-04-25
> **mbeach said:**
> are other machines on this same network?  do they exhibit the same behaviour?  Are you using some special dns servers?  If you have access to your DNS server, or router, try OpenDNS's dns server ips and see if you get the same behaviour.

opendns:
[https://www.opendns.com/start/](https://www.opendns.com/start/)

I have one other machine, the one I'm on now to do the USB stick and it does have the same problem.

I'll try this before I do the USB stick

---

### Post by mbeach on 2009-04-25
and if you need it, opendns's ip address:
[http://208.67.219.101/start](http://208.67.219.101/start)
(in case it is your dns server causing the issues)

---

### Post by albinootje on 2009-04-25
> **calebk said:**
> Yes, create usb unetbootin, if you can do it on a windows machine because the Linux version didn't work for me.

What went wrong exactly ? Just wondering.

```

chmod +x ./unetbootin-linux-323
sudo ./unetbootin-linux-323

```
still worked fine for me a few days ago.

---

### Post by toontastic on 2009-04-25
I used 208.67.222.222 and 208.67.220.220 was this wrong ?

---

### Post by calebk on 2009-04-25
Oh it worked for you! I tried a month and a bit ago so I remember what exactly went wrong. I think I just tried to write the Ubuntu software onto the usb flash drive and when I tried to run it on my netbook it wouldnt boot.

---

### Post by mbeach on 2009-04-25
no those are perfect.  I was just giving the [www.opendns.com](www.opendns.com) website ip in case you got redirected to some other site.  If the problem was your dns settings, then having the website's ip would get you to the right place.

---

### Post by toontastic on 2009-04-25
It looks like it was that as all seems to be working so far. I'm changing all my security settings on my router as I speak. I assume that would be the reason it changed or would there be another way ?

thanks for all the help everyone !

---

### Post by albinootje on 2009-04-25
> **toontastic said:**
> I used 208.67.222.222 and 208.67.220.220 was this wrong ?
Those are the DNS-server from OpenDNS.

From the OpenDNS website :
> 
The straight dope

Our nameservers are 208.67.222.222 and 208.67.220.220.


---

### Post by mbeach on 2009-04-25
no, it could be your isp's dns server got currupted and it had nothing to do with you, but good to have a good strong admin password on your router in any case.

---

### Post by albinootje on 2009-04-25
> **toontastic said:**
> It looks like it was that as all seems to be working so far.

Did you check which DNS-servers were in use before on your router or machines ?
If so, can you post them here ?

And I think it's a good idea to check whether your router is compromised or not.

---

### Post by toontastic on 2009-04-25
> **albinootje said:**
> Did you check which DNS-servers were in use before on your router or machines ?
If so, can you post them here ?

And I think it's a good idea to check whether your router is compromised or not.

Yeah I wrote them down they were:

85.255.116.67
85.255.112.149
1.2.3.4

---

### Post by albinootje on 2009-04-25
> **toontastic said:**
> Yeah I wrote them down they were:

85.255.116.67
85.255.112.149
1.2.3.4

Thanks. As you can perhaps see here :
```

# your old "flaky" DNS-servers previously in use :

$ host 85.255.116.67
67.116.255.85.in-addr.arpa domain name pointer 85.255.112.67.static.ukrtelegroup.com.ua.
$ host 85.255.112.149
149.112.255.85.in-addr.arpa domain name pointer 85.255.112.149.static.ukrtelegroup.com.ua.

# "good/normal" DNS-servers from your ISP :

$ host ns.ukrtelegroup.com.ua
Host ns.ukrtelegroup.com.ua not found: 3(NXDOMAIN)
$ host ns1.ukrtelegroup.com.ua
ns1.ukrtelegroup.com.ua has address 85.255.112.58
$ host ns2.ukrtelegroup.com.ua
ns2.ukrtelegroup.com.ua has address 93.188.161.58

```
The first two old DNS servers you were using seemed to be dodgy, and the DNS server number three (from your old list) is not even a valid ip public address afaik.

By the way, the WOT addon in Firefox gives [www.ukrtelegroup.com.ua](www.ukrtelegroup.com.ua) a "red" sign.

---

### Post by toontastic on 2009-04-25
> **albinootje said:**
> Thanks. As you can perhaps see here :
```

# your old "flaky" DNS-servers previously in use :

$ host 85.255.116.67
67.116.255.85.in-addr.arpa domain name pointer 85.255.112.67.static.ukrtelegroup.com.ua.
$ host 85.255.112.149
149.112.255.85.in-addr.arpa domain name pointer 85.255.112.149.static.ukrtelegroup.com.ua.

# "good/normal" DNS-servers from your ISP :

$ host ns.ukrtelegroup.com.ua
Host ns.ukrtelegroup.com.ua not found: 3(NXDOMAIN)
$ host ns1.ukrtelegroup.com.ua
ns1.ukrtelegroup.com.ua has address 85.255.112.58
$ host ns2.ukrtelegroup.com.ua
ns2.ukrtelegroup.com.ua has address 93.188.161.58

```
The first two old DNS servers you were using seemed to be dodgy, and the DNS server number three (from your old list) is not even a valid ip public address afaik.

By the way, the WOT addon in Firefox gives [www.ukrtelegroup.com.ua](www.ukrtelegroup.com.ua) a "red" sign.

hmmmmmm my ISP is Virgin Media. So does that mean the problem has occurred at my end ?

---

### Post by albinootje on 2009-04-25
> **toontastic said:**
> hmmmmmm my ISP is Virgin Media. So does that mean the problem has occurred at my end ?
Your router could have been compromised, which is kind of likely since you mentioned that your other machine had the same problems.

The dodgy DNS-servers were originating from the former USSR, your ISP seems to be in the UK though.

A search for the dodgy ip addresses showed this :

[http://www.net-security.org/article.php?id=1150](http://www.net-security.org/article.php?id=1150)
Please make sure to thoroughly check your adsl-router or cable-modem!

---

### Post by toontastic on 2009-04-26
Thanks for that, hopefully I'm all locked down now. My wireless is now hidden, with new passwords on the login via the web and also better passwords on the WPA key. Fingers crossed I'm more secure.

---

### Post by telmac on 2009-04-26
oh NO! my nightmares of viruses on windows have gone now that I use Ubuntu, but this might mean that the nightmares will come back!!!!!!!

speaking of that what will happen if I went to goggle (not google, I am talking about the virus website) on my ubuntu machine? Will I be immune?

---


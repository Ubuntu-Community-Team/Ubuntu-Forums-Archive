---
title: "[SOLVED] Trouble loading the Ubuntu Forums"
date: 2007-09-01
forum: Forum Feedback &amp; Help
---

### Post by runemaste644 on 2007-09-01
I'm having trouble loading the Ubuntu Forums in Opera and Konqueror, sometimes all browsers wont load it correctly.

In Opera (and when all other browsers don't work) i get something like this picture and it says things like "/showthread.php? wasn't found on this server" "/newthread.php? wasn't found on this server"

Konqueror just wont load images on any web page. It loads the page, but no images.

edit: It does in firefox too

---

### Post by runemaste644 on 2007-09-03
i think it is something with this stupid pshells thing. Sum1 help me

---

### Post by runemaste644 on 2007-09-03
aargh its doing it again... WHY WONT IT STOP?!

---

### Post by ubuntu-geek on 2007-09-04
I would contact the people who run pshells.. It appears to be a problem with them not us :)

---

### Post by runemaste644 on 2007-09-04
Today its being active on bumping me off. I guess i could email them.

---

### Post by runemaste644 on 2007-09-04
It just does that on my laptop. It works fine on any other computer...

---

### Post by FuturePilot on 2007-09-05
Can you reproduce this on your laptop with a live CD?

---

### Post by runemaste644 on 2007-09-05
I feel nervous that i might format my HDD by accident with a live CD... i guess it is only my computer

---

### Post by FuturePilot on 2007-09-05
As long as you don't click Install, your hard drive will be fine. Even if you did it wouldn't do anything until you fill out all the necessary information.

---

### Post by runemaste644 on 2007-09-06
It is working today. Maybe it got fixed.

---

### Post by runemaste644 on 2007-09-08
Oops! i almost forgot to mark it as solved!

---

### Post by runemaste644 on 2007-09-09
Its doing it again. Even on all my other computers. This time i entered 82.211.81.186 and it worked.

---

### Post by FuturePilot on 2007-09-10
Maybe a DNS issue?:confused:

---

### Post by runemaste644 on 2007-09-10
I think it has to do with updates. But i dont mind putting in 82.211.81.186.

---

### Post by runemaste644 on 2007-09-10
Off topic: Bean quote upgrade!!
I remember when all your coffee cups ran away, too.

---

### Post by FuturePilot on 2007-09-11
> **runemaste644 said:**
> Off topic: Bean quote upgrade!!
I remember when all your coffee cups ran away, too.

:lolflag:

I wonder what type of update would have done that. :-k

---

### Post by runemaste644 on 2007-09-15
Allright, the IP of the page changed, but now another site kicked in (it went away pretty quickly). Heres another screenshot

---

### Post by PriceChild on 2007-09-16
Yes, Canonical recently changed the ip of the forums to help with some routing problems iirc.

---

### Post by jdong on 2007-09-17
Hey everyone, I've been noticing huge response delays on my side too... We're looking into the problem at the moment. Thanks for your patience.

---

### Post by FuturePilot on 2007-09-17
> **jdong said:**
> Hey everyone, I've been noticing huge response delays on my side too... We're looking into the problem at the moment. Thanks for your patience.

Yes, it's painfully slow for me too.

---

### Post by ubuntu-geek on 2007-09-17
The server was being attacked :) ATM it seems to be ok.

---

### Post by jdong on 2007-09-17
Ok, the problem has been identified (denial-of-service/hammering) and is being corrected atm...

---

### Post by FuturePilot on 2007-09-17
> **ubuntu-geek said:**
> The server was being attacked :) ATM it seems to be ok.

Attacked!?:-s Would that be related to distrowatch being down?
It's weird because it will be fast one moment and then it just slows to a crawl the next. It's even refused to connect sometimes. I get the old, Cannot connect to [http://ubuntuforums.org](http://ubuntuforums.org), the server may be busy, blah, blah message.

---

### Post by ubuntu-geek on 2007-09-17
Not sure if its related to be honest.

---

### Post by runemaste644 on 2007-09-23
Its fixed! i added > 0.0.0.0 [www.poczta.skomur.pl](www.poczta.skomur.pl) to /etc/hosts

---

### Post by runemaste644 on 2007-09-23
or not. I am blocking cookies from ubuntuforums.org currently and it is working

---

### Post by runemaste644 on 2007-09-23
Now were getting somewhere. I should get```
[SIZE=3]64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=1 ttl=50 time=126 ms[/SIZE]
``` when pinging ubuntufoums.org but i am being hijacked at DNS level so i sometimes get```
[SIZE=3]64 bytes from kuzyn.netburg.pl (91.189.0.4): icmp_seq=1 ttl=31 time=187 ms[/SIZE]
``` Why would a polish email service hijack me?

---

### Post by arijarot on 2007-11-23
What is ohiggins.canonical.com? My vmware (vmnet-nat) has many connections (LAST_ACK) to it and it's not even running.

---

### Post by PriceChild on 2007-11-23
It is the server that the forums are hosted on.

---

### Post by arijarot on 2007-11-23
> **PriceChild said:**
> It is the server that the forums are hosted on.

Oh, OK. Thank you. Do you know why vmware's vmnet-nat would have at least 20 connections (last _ack) with it? (when vmware is not even on?)

---

### Post by jdong on 2007-11-25
> **arijarot said:**
> Oh, OK. Thank you. Do you know why vmware's vmnet-nat would have at least 20 connections (last _ack) with it? (when vmware is not even on?)


It's an incompletely torn down connection (still awaiting the final FIN_ACK which terminates the connection formally) -- most likely an artifact of an abrupt VMWare shutdown or just buggy vmware type network interface drivers.

Unless you are a router admin and see a sudden spike up to the thousands of these from a single user, there's nothing to worry about (there do exist LAST_ACK denial of service attacks with the symptoms I just mentioned; but it's quite rare)

---

### Post by arijarot on 2007-11-25
> **jdong said:**
> It's an incompletely torn down connection (still awaiting the final FIN_ACK which terminates the connection formally) -- most likely an artifact of an abrupt VMWare shutdown or just buggy vmware type network interface drivers.

Unless you are a router admin and see a sudden spike up to the thousands of these from a single user, there's nothing to worry about (there do exist LAST_ACK denial of service attacks with the symptoms I just mentioned; but it's quite rare)

Thanks for the info, jdong. That helps :)

---


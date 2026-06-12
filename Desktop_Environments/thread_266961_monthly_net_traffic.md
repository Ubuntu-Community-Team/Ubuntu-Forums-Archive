---
title: "monthly net traffic"
date: 2006-09-28
forum: Desktop Environments
---

### Post by drtvasudevan on 2006-09-28
i have an adsl connection with a monthly cap of one gig.
there are free hours from 2am to 8 am -the traffic during that time is not counted.

what i need is an apllication that keeps track of the traffic and lets me know how much i have used during non free hours.
pl let me know which one.
thanks in advance
8) 
tv

---

### Post by amohanty on 2006-09-28
Search for bandwidthd and tcptrack in synaptic.

HTH
AM

PS: also look at rtg, mrtg and other snmp tools

---

### Post by Josh1 on 2006-09-28
If you just have linux and thats all (like 1 computer with linux), you can just use firestarter. Its a firewall AND tells you how much incoming and outgoing traffic you have used!
Also, maybe your ISP has a page on their site telling you how much bandwidth you have used?

To install firestarter:
```
sudo apt-get install firestarter
```

---

### Post by drtvasudevan on 2006-09-28
thanks. will do
tv
> **amohanty said:**
> Search for bandwidthd and tcptrack in synaptic.

HTH
AM

PS: also look at rtg, mrtg and other snmp tools

---

### Post by drtvasudevan on 2006-09-28
> **Josh1 said:**
> If you just have linux and thats all (like 1 computer with linux), you can just use firestarter. Its a firewall AND tells you how much incoming and outgoing traffic you have used!

will try if the otherones are not satisfactory.

> Also, maybe your ISP has a page on their site telling you how much bandwidth you have used?



the less said the better.
[-( 
first they want ONLY  internet explorer in that site.
:evil: 
otherwise one cant see it.
they show the total volume.
not segregated as free non free
:confused:

---

### Post by Ramses de Norre on 2006-09-28
One Gig?? That's not much.. A default acount here in Belgium has 10 Gig.

---

### Post by amohanty on 2006-09-28
> first they want ONLY internet explorer in that site.

FF has a extension called user-agent switcher which will let you fake out the site, unless of course they use some active-x crap, in which case, run...

AM

---

### Post by drtvasudevan on 2006-09-28
will seriously consider migrating to belgium. :D 

> **Ramses de Norre said:**
> One Gig?? That's not much.. A default acount here in Belgium has 10 Gig.

---

### Post by drtvasudevan on 2006-09-28
> **amohanty said:**
> Search for bandwidthd and tcptrack in synaptic.

PS: also look at rtg, mrtg and other snmp tools
installed bandwidthd and later mrtg.
but where are they?
i dont see them in the menu nor the debian menu
how do i invoke them and get details?
:confused:

---

### Post by amohanty on 2006-09-29
bandwidthd details and forums here:
[http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

mrtg:
[http://oss.oetiker.ch/mrtg/doc/index.en.html](http://oss.oetiker.ch/mrtg/doc/index.en.html)

You will have to use the terminal to invoke them. Also bandwidthd is a daemon, so it runs in the background and should have a copy in /etc/init.d

HTH
AM

---

### Post by drtvasudevan on 2006-10-08
thanks mohanty.
could you please give the commands to invoke it?
the bandwidthd website is not vey helpful.
tv
edit:
and there is no report in init.d folder. it is full of shell scripts.
oh, you mean i can launch it from there?
ok
> **amohanty said:**
> bandwidthd details and forums here:
[http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

mrtg:
[http://oss.oetiker.ch/mrtg/doc/index.en.html](http://oss.oetiker.ch/mrtg/doc/index.en.html)

You will have to use the terminal to invoke them. Also bandwidthd is a daemon, so it runs in the background and should have a copy in /etc/init.d

HTH
AM

---

### Post by amohanty on 2006-10-08
Sorry I assumed you were familiar with linux services and stuff. Anyway I have attached the README that comes with bandwidthd source. Take a look at that and let me know if you dont get anything. 

Also if you are not very familiar with setting up fairly complex daemons based on database backaneds, I would suggest going with mrtg.

HTH
AM

---

### Post by drtvasudevan on 2006-10-09
mistake is mine
i should have mentioned that i am a non I-tech person (an anesthetist)
i shall look into it after 12th which is a translation deadline for ubuntu
thanks for the interest.

> **amohanty said:**
> Sorry I assumed you were familiar with linux services and stuff. Anyway I have attached the README that comes with bandwidthd source. Take a look at that and let me know if you dont get anything. 

Also if you are not very familiar with setting up fairly complex daemons based on database backaneds, I would suggest going with mrtg.

HTH
AM

---


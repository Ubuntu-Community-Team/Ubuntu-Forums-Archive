---
title: "can't get one particular webpage... weird!"
date: 2009-01-02
forum: General Help
---

### Post by cornflake000 on 2009-01-02
This is probably the most ridiculous question I have ever asked on this or any forum.  Please forgive me for this but I am completely baffled.

There is one single web page on the planet that I have not been able to access for 3 months now.  I can get it from every other network I have had access to but not here. on mine.  I have checked the router... even changed from one router to another, checked all settings even tuned off firewall screening without success.  I can also get any other website that is accessible in the world but not... [http://www.delta.com](http://www.delta.com) which is Delta Airlines as a matter of fact.  The pages are .jsp which is not a problem....

I am stumped.  I don't know if it's an Ubuntu Intrepid issue or a firefox issue.  No Web browser works, no operating system works M$ or Linux.  I have 4 different Linux OS's.  I have my own network setup... static.  My IP is simply a bridge, no extras.  

Does anyone have any idea where this could come from? 

PS.  please don't laugh!  I'm going bald over this.

---

### Post by ajcham on 2009-01-02
Have you tried asking your ISP? They might be able to shed light on the matter.

---

### Post by 2hot6ft2 on 2009-01-02
Are you perhaps running a p2p app that has a blocklist loaded? Maybe it's blacklisted.

---

### Post by Sami_Sdata on 2009-01-02
You say you have a static IP.  Any chance you could post that IP?  It sounds more like someone is blocking at some point. A traceroute from your computer to delta.com would also help.

;; ANSWER SECTION:
[www.delta.com](www.delta.com).          3600    IN      CNAME   delta.com.
delta.com.              3600    IN      A       205.174.16.50

The web page only resolves to one IP wherever I test it from.  

 I only see three providers connecting direct to Delta.com
Savvis
Global Crossing
Internap


Seeing were the trace dies might help.

---

### Post by dcstar on 2009-01-02
> **cornflake000 said:**
> This is probably the most ridiculous question I have ever asked on this or any forum.  Please forgive me for this but I am completely baffled.

There is one single web page on the planet that I have not been able to access for 3 months now.  I can get it from every other network I have had access to but not here. on mine.  I have checked the router... even changed from one router to another, checked all settings even tuned off firewall screening without success.  I can also get any other website that is accessible in the world but not... [http://www.delta.com](http://www.delta.com) which is Delta Airlines as a matter of fact.  The pages are .jsp which is not a problem....

I am stumped.  I don't know if it's an Ubuntu Intrepid issue or a firefox issue.  No Web browser works, no operating system works M$ or Linux.  I have 4 different Linux OS's.  I have my own network setup... static.  My IP is simply a bridge, no extras.  

Does anyone have any idea where this could come from? 

PS.  please don't laugh!  I'm going bald over this.

```
traceroute www.delta.com
```
or even better:
```
tcptraceroute www.delta.com 80
```

---

### Post by sofasurfer on 2009-01-02
This would make an interesting thread... Are there any web sites that you can not access?

If I go to [www.clickondetroit.com](www.clickondetroit.com) and then click on "Fast Cast", I cannot access any of the video links under the video screen. When I click on them my browser immediately closes.

Other links on the web site work fine.

---

### Post by dcstar on 2009-01-02
> **sofasurfer said:**
> This would make an interesting thread... Are there any web sites that you can not access?

If I go to [www.clickondetroit.com](www.clickondetroit.com) and then click on "Fast Cast", I cannot access any of the video links under the video screen. When I click on them my browser immediately closes.

Other links on the web site work fine.

That is just bad web page coding (made and tested with IE and Windows), unfortunately it is not uncommon as too many places still do not support the open web standards.

---

### Post by cornflake000 on 2009-01-03
Wow, thanks for all the posts!

I have checked my blacklist...
I have checked the internet block lists...
I have checked with my IP but they don't have anything to do with it.  Qwest.
I have called the airline...
I have done all the tracing and pinging and domain checking that I can do.

Any other ideas?

Thanks!!

---

### Post by Sami_Sdata on 2009-01-03
> **cornflake000 said:**
> Wow, thanks for all the posts!

I have checked my blacklist...
I have checked the internet block lists...
I have checked with my IP but they don't have anything to do with it.  Qwest.
I have called the airline...
I have done all the tracing and pinging and domain checking that I can do.

Any other ideas?

Thanks!!

 You could post the traces and your IP so we can test from our sides.  The problem could be on the return path back to you.

---


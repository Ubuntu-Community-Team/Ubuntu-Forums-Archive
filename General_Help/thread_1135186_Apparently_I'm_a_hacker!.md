---
title: "Apparently I'm a hacker!"
date: 2009-04-24
forum: General Help
---

### Post by Free Thinker on 2009-04-24
When I try to visit this site [http://www.linux-tutorial.info/](http://www.linux-tutorial.info/) I get redirected to a page containing the following text:

> 
You have been blocked from entering this site.

You have attempted an unknown attack on this site.

All of the following information has been gathered to assist the webmaster should this need to be reported to local or federal law enforcement.

Because of the insecure nature of the internet and the increase in attacks, it is unfortunately possible that the security mechanisms have indicated an attack when it really is not. If you think this is a mistake you can contact the site webmaster at linkbat_admin(at)linux-tutorial(dot)info.

Be SURE to include the following information in any email!
User Agent: Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.8) Gecko/2009032711 Ubuntu/8.10 (intrepid) Firefox/3.0.8
Query String:
GET String:
POST String:
Referer: none
Request Method: GET
Remote Address: myipaddress
Client IP: none
Forwarded For: 127.0.0.1
Date Blocked: 2009-04-24 @ 13:32:52 CEST GMT +0200
Block expires: Permanent
NukeSentinel(tm) 2.0.1 by: NukeScripts.net

I've contacted the webmaster and he sent a friendly email back:

> The message was caused by these two entries:

Client IP: none
Forwarded For: 127.0.0.1

This is a very common method for hackers to hide their tracks. Unfortunately,
this is the default configuration for many proxy services and as a result,
they get blocked although no real attack took place. However, in my opinion
it is problem with the configuration of the proxy server.

The police are more likely to stop someone who is unshaven, uncombed, and is
wearing dirty clothes than someone who is clean-shaven and wearing a suit. It
might be unfair, but considering that I get several attempted attacks every
single day (that I catch), I am not happy with turning off any of the
security, especially when it is caused by (in my opinion) improper
configuration of the proxy server.

Please note that if other sites prevent attacks in this way, you
will get blocked from them as well.

Regards,

Can anyone explain what's going on here? I'm using an institution's network proxy rather than my own house, is this a problem with the set up of the proxy server, or my computer?

I'm not even remotely adept at using Linux, let alone hacking into other computers!

---

### Post by StuartN on 2009-04-24
> **Free Thinker said:**
> Can anyone explain what's going on here? I'm using an institution's network proxy rather than my own house, is this a problem with the set up of the proxy server, or my computer?

It sounds like your school setup is at fault - when you browse the web, the proxy server downloads whatever you browse, but seems to strip off your IP address. The purpose of the proxy is to cache stuff so it loads faster, with less bandwidth, when other people in the school access the same stuff.

---

### Post by sgtbug on 2009-04-24
Looks like a proxy problem.. similar thing happened with me once.. some sites won't let me in from my college's network.. i reported it to them and they corrected the problem.. there seems to be some sort of filtering in the system i think.. Contact the institution's system admin..

sorry for not being of much help..

---

### Post by James_Lochhead on 2009-04-24
> **Free Thinker said:**
> Can anyone explain what's going on here? I'm using an institution's network proxy rather than my own house, is this a problem with the set up of the proxy server, or my computer?

I'm not even remotely adept at using Linux, let alone hacking into other computers!

This is a problem with the proxy server, it is nothing to do with Linux. I would forward the email to them along with the message you got to see if you can get the problem resolved.

---

### Post by nandemonai on 2009-04-24
As others have stated, your proxy is hiding its IP, that's all it is ;)

---

### Post by James_Lochhead on 2009-04-24
Oh by the way you might want to use the term cracker for this in the future. 

The term hacker originally meant someone who is very technically adept at computing and has a slight disregard for authority.

The media got hold of the term and turned it in to someone who gains unauthorized access to a computer system. Previously the word for this was cracker.

If you use the term hacker it might (initially) confuse some of the old schoolers (old farts :-D) who still only use the original meaning of hacker.

---

### Post by garion42 on 2009-06-11
What would be proper values for "Client IP" and "Forwarded For"? Where this is done is naturally an issue for the respective proxy, but what values would be appropriate?

---

### Post by benj1 on 2009-06-11
> **James_Lochhead said:**
> Oh by the way you might want to use the term cracker for this in the future. 

The term hacker originally meant someone who is very technically adept at computing and has a slight disregard for authority.

The media got hold of the term and turned it in to someone who gains unauthorized access to a computer system. Previously the word for this was cracker.

If you use the term hacker it might (initially) confuse some of the old schoolers (old farts :-D) who still only use the original meaning of hacker.
+1 although im not an old fart

---


---
title: "Certificate page stopping &quot;my.yahoo&quot; sign-in!"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Neobuntu on 2006-06-01
What do I do? It says some odd site is perhaps trying to steal the password I'm about to enter.

Why didn't that last version of Firefox do this?

I Installed the new Dapper 1.5.0.3 Firefox.

Konqueror didn't ask and I don't know if that's good or bad.

Do I need to somehow install certificates? or what?

I'm guessing it's not Yahoo but a installation componet I need and I can't use Firefox until I'm sure it's not a counterfeit site (verifying yahoo sign-in) .

---

### Post by Neobuntu on 2006-06-01
We can't even use Firefox to retrive email until we find a solution. I can't find anything via a search.

---

### Post by Neobuntu on 2006-06-01
I can guess this is a configuration problem but don't know what to do next.

Does anyone know if Yahoo now doesn't work with Firefox?

---

### Post by NeoChaosX on 2006-06-02
Just go to [http://mail.yahoo.com](http://mail.yahoo.com).  That works fine in Firefox.

---

### Post by Neobuntu on 2006-06-02
Nope (but thanks.) I get the same scarry message.

What it the world is going on? How would Firefox know to pass this now suspect certificate in the first place? 

Now in says "login.yahoo.com", before it was something weird.

It says it's certified from Equifax which sounds fine but then WHY is it start asking me this now. The expiration seems to be in 2011.

ALL my other issues are resolved tonight (and I helped some people too) but this has me in the dark. What's missing?

Help please?

---

### Post by towsonu2003 on 2006-06-02
If it is saying something like 
> 
The site &#8220;mail.yahoo.com&#8221; returned security information for &#8220;login.yahoo.com&#8221;. It is possible that someone is intercepting your communication to obtain your confidential information.

You should only accept the security information if you trust &#8220;mail.yahoo.com&#8221; and &#8220;login.yahoo.com&#8221;.

just hit ok/accept and it will load the page. 

If it's something else, please copy paste the dialog. 

This (above message) happens to me everytime when I go to http**s**://mail.yahoo.com -this is because of yahoo, not firefox. the same dialog (with a different language) will appear if I go there with Internet Explorer and Epiphany (above dialog is taken from epiphany). 

It is basically saying that mail.yahoo.com's certificate info doesn't match its own address. it's ok as long as it matches login.yahoo.com... weird stuff [-(

---

### Post by Neobuntu on 2006-06-02
Well thank you very much. You understand just what I'm wondering.

I suppose it's been a while since I started Firefox completely anew. Maybe that's all it is.

Still, scarry stuff. If it was a spoof (and these are on the rise) how would I know. I mean, it seems like it's warning me that somthings wrong and like a mook, I just ignore it. ...Never a good thing.

Anyone know for sure?

---

### Post by rcarring on 2006-06-02
Without hardly any exception FF, Moz and even SM have been getting pissy about https:// addresses and waving an alert box at me about the certificate. IE6 doesn't mind the certificate, IE6 running on Wine doesn't care either.

Incidentally, mail.yahoo.com beta ONLY works with XP2 and IE6, any other OS or browser it says its not supported and you can go back to using the old interface.

---

### Post by Neobuntu on 2006-06-02
Nice move Yahoo. Bye Yahoo and all my clients are going with me. I'm Sick of the ads anyway.

Smooth move Yahoo! You just lost around 25% of your users. 50% by next year, etc. 

Do you Yahoo. Reputation is a bi-ch.

You know, all these Microsoft loving companies are betting we don't have a memory. The bandwagon might be full of this brand of poo when they're the last to catch on.

---

### Post by MattCarp on 2006-06-02
I'm having the same problem at other web sites - ebay.com, tdameritrade.com.

It appears that Firefox 1.5.0.3 does not trust the RSA Data Security certificate authority?

What's interesting is that when I go to the Firefox CA page (Edit>Preferences>Advanced>View Certificates>Authorities) it's blank.  That is, I don't see any CA's.

I'm tempted to export all of them from IE6, e-mail them over, and import them into Firefox.

-Matt

---

### Post by GQed76 on 2006-06-02
1.5.0.4 was released for windows...hrrrm

---

### Post by MattCarp on 2006-06-02
This is the same topic, and is better described in thread [http://ubuntuforums.org/showthread.php?t=186440](http://ubuntuforums.org/showthread.php?t=186440)

btw, I was able to fix it by reinstalling all of the relevant packages (notably firefox and  libnss3, but also firefox-gnome-support, gnome-app-install, mozilla-firefox, 
yelp at the same time)

-Matt

---


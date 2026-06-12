---
title: "Flash plugin not working with certain website?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by JeffBlouin on 2006-09-17
Hi

  I installed flash pluging for firefox and it's working fine almost everywhere excepr on certain website. When i try to log on: 
[www.themovienetwork.ca](www.themovienetwork.ca) , I get thismsg: themovienetwork.ca requires you to install the lattest Adobe Flash Player Click Here to Get Flash

But it's really installed

Any idea?
Anyone can check and see if the problem is with me or with the website?

THANKS
jEFFBlOUIN

---

### Post by whizbaby on 2006-09-17
Open a terminal and type
**less .mozilla/firefox/pluginreg.dat**
look for a line similar to this

Shockwave Flash 7.0 r**63**:$

This is mine and I cannot connect the page getting the same error **because**:
my (and perhaps yours, too) version is an older version of the flash player, namely 7.0.**63**! If it doesn't show r68 install the new version.

---

### Post by JeffBlouin on 2006-09-17
Thanks
I think I have the lattest version installed:

> /usr/lib/firefox/plugins/libflashplayer.so:$
:$
1158524954000:1:5:$
Shockwave Flash 7.0 r68:$
Shockwave Flash:$


Any other idea?

---

### Post by someguyouknow on 2006-09-17
The newest version is 8.5 or 9 i believe. its not available for Linux right now but you can trick some sites by just changing the 7.0 to 9.0.
i dont know the consequences though...

---

### Post by JeffBlouin on 2006-09-17
Simple as that!

And where exactly do I change that?

Thanks

---

### Post by Anduu on 2006-09-18
I have used that trick  but it won't work all the time...this is one of those times.

---

### Post by DoktorSeven on 2006-09-18
Your only real solution until Flash 9 is released for Linux (and who knows how long that will be) is to use Wine to install Windows Firefox and Flash 9 (for Windows), then run Windows Firefox to view Flash 8/9 pages.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) has a writeup on how this is done.

---

### Post by JeffBlouin on 2006-09-22
Thanks, I will try that!

Jeff

---


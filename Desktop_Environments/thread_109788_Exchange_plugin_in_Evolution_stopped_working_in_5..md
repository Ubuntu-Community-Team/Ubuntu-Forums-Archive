---
title: "Exchange plugin in Evolution stopped working in 5.10"
date: 2005-12-29
forum: Desktop Environments
---

### Post by FidelTheInfidel on 2005-12-29
In the 5.10 the Evolution and the Exchange plugin do not work for me. Just like on my other working box (5.04) I fill the account info (MS Exchange server) but it tries to contact some rubbish URI instead (not the one I type in, not the one it shows there). If I compare the .gconf/apps/evolution/mail/%gconf.xml on 5.04 again 5.10 I can see that instead of (e.g. imaginary one):
```
<url>exchange://infidel.fidel@abcde123.domain.com
```
there is twice:
```
<url>exchange://infidel.fidel@abcxz123.domain.com
```

and of course, there is no such abcxz123. Any ideas? I happily access that Exchange server from 5.04 but no chance from 5.10 and this really hurts:confused: 


Summary:
evolution-exchange 2.4.1-0ubuntu1
evolution 2.4.1-0ubuntu7

---

### Post by vtec on 2006-01-03
I just started using exchange in 5.10, so i'm not sure how it was. But i do know that for me in 5.10 i have had nothing but problems. The exchange plugin is very buggy.

---

### Post by N6546R on 2006-01-03
I had to stop using Evolution in 5.10, as it was permanently losing emails and appointments. There've been a few notes in this forum hinting that the Dapper release will be much more solid.

Perry

---

### Post by mikecrowe on 2006-01-03
I wanted to try and install 2.5.3 of Evolution, but I ran into some problems.  First, when trying to compile some sources, I got:
> ../../calendar/gui/e-cal-model.h:145: warning: type defaults to 'int' in declaration of 'ECalComponentId'
../../calendar/gui/e-cal-model.h:145: error: syntax error before '*' token
So then, I thought I'd try and grab the compiled 2.5.3 from DapperDrake.  Added it to my repositories and gave it a whirl.  Way too many upgrades to libraries for my comfort. 

Anybody have any suggestions?  I *must* get this working or my IT guy will force me to go back to XP (shudder).

Please!
TIA
Mike

---

### Post by fonva on 2006-01-03
Where can I get the evolution-exchange package?

---

### Post by mikecrowe on 2006-01-03
[QUOTE=fonva]Where can I get the evolution-exchange package?[/QUOTE]

It was installed on Breezy.

---

### Post by libertyaikido on 2006-01-05
[QUOTE=mikecrowe]I wanted to try and install 2.5.3 of Evolution, but I ran into some problems.  First, when trying to compile some sources, I got:

So then, I thought I'd try and grab the compiled 2.5.3 from DapperDrake.  Added it to my repositories and gave it a whirl.  Way too many upgrades to libraries for my comfort. 

Anybody have any suggestions?  I *must* get this working or my IT guy will force me to go back to XP (shudder).
Mike[/QUOTE]

Same here.  Any suggestions.

---

### Post by jadajada on 2006-01-05
Just giving this a bump... Evolution-exchange is now the only reason for me not using Ubuntu. I always fall back to Debian Testing (Etch), where evolution-exchange works perfectly! From time to time I try to install Breezy, hoping this issue is fixed. But it's not. Am I right in assuming that this will never be fixed in Breezy? Should we just give up for now and wait for Dapper?

Is there some backport of evolution-exchange that is usable on Breezy? I have read some other posts stating that evolution-exchange is working in Dapper.

This is really a shame, because I really like Ubuntu, but I _have_ to get the plugin going for accessing our Win2000 Exchange server at work. I know I can use imap, which actually works, but I like to get everything, email, global address list and calendar.

So is there hope?:neutral:

---

### Post by vtec on 2006-01-05
What are the versions in debian testing that are working. Is it the version packaged in ubuntu that is broken, or is it the package that is broken its self.

---

### Post by mikecrowe on 2006-01-05
Guys, 

I've solved this for me.  Turns out my issue was an MTU issue.  I'm not sure if my VPN software exaggerated this or not, but by doing an: > ifconfig eth1 mtu 1300I was able to instantly connect.  All my problems solved.

---

### Post by jadajada on 2006-02-22
To answer the question above. Debian Testing has now made leaps forward with its packages. Among other upgrades, Evolution got updated to 2.4, and guess what? Now Evolution Exchange is broken there too... So it's not an Ubuntu spesific issue. 

A downgrade through snapshot.debian.org brought back evolution 2.2, which is working.

Now... Does this work in Dapper? Anyone know?

---

### Post by vtec on 2006-02-22
I read somewhere that it was working.... I hope this is true.

---

### Post by jadajada on 2006-02-23
[QUOTE=mikecrowe]Guys, 

I've solved this for me.  Turns out my issue was an MTU issue.  I'm not sure if my VPN software exaggerated this or not, but by doing an: I was able to instantly connect.  All my problems solved.[/QUOTE]


I tried this solution as well. No change. Still broken Evolution Exchange.

---

### Post by glorry on 2006-02-23
[QUOTE=jadajada]Just giving this a bump... Evolution-exchange is now the only reason for me not using Ubuntu. I always fall back to Debian Testing (Etch), where evolution-exchange works perfectly! From time to time I try to install Breezy, hoping this issue is fixed. But it's not. Am I right in assuming that this will never be fixed in Breezy? Should we just give up for now and wait for Dapper?

Is there some backport of evolution-exchange that is usable on Breezy? I have read some other posts stating that evolution-exchange is working in Dapper.

This is really a shame, because I really like Ubuntu, but I _have_ to get the plugin going for accessing our Win2000 Exchange server at work. I know I can use imap, which actually works, but I like to get everything, email, global address list and calendar.

So is there hope?:neutral:[/QUOTE]

For me it is almost same:
in ms Windows, outlook2003, i can put my exchange server like: ppp.xxx.com
but in my Evolution Mail setting in Utunbu, after select MS Exchange Server, it pompt to enter User Name and OWA Url, if OWA Url entered like: ppp.xxx.com, can not select 'Authenticate', if entered: 'http://ppp.xxx.com', 'Authenticate' can be pressed but soon said 'url or user or pwd' error.

I think it must be a BUG in Utunbu of Evolution Mail.

---

### Post by glorry on 2006-02-23
Which way did you solve it?

---

### Post by LittleLebowski on 2006-02-25
Any thoughts here?  The MTU fix did not work for me.  ANybody know if there's a  bug report filed?  This is CLEARLY not working in Breezy.

---


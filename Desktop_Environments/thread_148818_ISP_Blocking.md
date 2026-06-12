---
title: "ISP Blocking?"
date: 2006-03-22
forum: Desktop Environments
---

### Post by mcrofutt on 2006-03-22
Hi all,
 Here's a new one. Is it possible for my ISP to block my firefox and evolution from their site? I've tried on numerous occasions to access both and I get timed out. I've also seen the same thing with firefox on the Mozilla site. I can access all of the above from my Windows partition, using firefox and OE. If you need more info, I'll be happy to oblige.
 Thanks in advance, Marcus.

---

### Post by Horndog on 2006-03-22
Has firefox and evolution ever worked?

---

### Post by mjwood0 on 2006-03-22
I highly doubt that your ISP could block specific browsers or e-mail clients.

I'm not 100% sure, but I really don't believe that the ISP can tell which browser or E-Mail client you use.

(Note: In actuality, the ISP could determine which browser you are using.  However, I doubt their routers are doing this.  Routers are designed to run as fast as possible and I think sorting all this information just to determine whether or not to drop a packet would be a HUGE slowdown.)

I'm guessing you have a configuration problem.  Can you ping a site from the command line?

What's the output of: 
```
ping www.ubuntuforums.org
```

---

### Post by mcrofutt on 2006-03-22
Thanks for the quick replies!!!!!
 I'm using Firefox to reply to ya'll now, so yes it works. I've used the same ISP since installing Ubuntu and have not been able to access their site since. Perhaps I have something screwed up? I can access MOST other web sites. Mozilla.org will NOT connect, nor will the Firefox page. Others though are no problem. 
 I've sent a ping to ubuntuforums.org and never got any results from cli. Just a blinking cursor.
 A ping to Yahoo.com displayed LOTS of hits.
PING yahoo.com (216.109.112.135) 56(84) bytes of data.
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=1 ttl=55 time=209 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=2 ttl=55 time=177 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=3 ttl=55 time=180 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=4 ttl=55 time=195 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=5 ttl=55 time=177 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=6 ttl=55 time=180 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=7 ttl=55 time=178 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=8 ttl=55 time=177 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=9 ttl=55 time=181 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=10 ttl=55 time=193 ms

 and then some,,,,lol 
 I hope this helps you help me,,,,,:-)
 Thanks !!!!!
 Marcus

---

### Post by joshuapurcell on 2006-03-22
I live in Grand Prairie (NE Texas), and my ISP is currently Grande Communications (and I'm using the connection without any problems at all). I can almost guarantee that your ISP is not causing these problems... but what is your ISP's name?

---

### Post by NeghVar on 2006-03-22
Just for the record, your ISP most likely knows what your operating system is and your basic specs, at least they knew when I used windows with what hardware.

---

### Post by mcrofutt on 2006-03-22
Again thanks for the quick replies!
 I'm using Sysmatrix.net out of Silsbee,Texas. I'm located in extreme NE Texas, about 25 miles from Arkansas, and Louisiana, near Texarkana.

---

### Post by FIONEX on 2006-03-22
First of all, if you can ping your ISP website from within linux, then it's a browser problem.  If you can't, then it's DNS cache problem and nothing more.  If it's coming down to a browser problem, it could be just about anything, but I've seen many scripts that only load pages for Windows users.  You can try faking the User-Agent command that the browser sends by getting the UserAgent Switcher extention for firefox.  If it's a DNS Cache problem, it should clear automatically, else you should look up a way to clear it on your own.  I know for example in windows, if you try to load a website while the server is down, the DNS cache will put that in the cache as the website is unreachable.  Then you're gonna have to restart the PC until the DNS cache is cleared or you can do "ipconfig /cleardns".  I'm not sure of the equivalent for linux.

---

### Post by mcrofutt on 2006-03-26
Bumping this up as I still haven't an answer to solve this.

---

### Post by bradlis7 on 2006-03-30
I've looked up how to clear the dns cache on linux, and from what I've seen, linux does not cache the dns. I can't get to my own website right now because of a recent move of servers, but I can get it with a proxy site (e.g. [https://www.megaproxy.com/freesurf/)](https://www.megaproxy.com/freesurf/)). It's really quite annoying... I can't even check my email.

EDIT: Finally! Right after I posted it allowed me to go there.

---


---
title: "New to Ubuntu - Can't visit asp.net web page"
date: 2008-12-14
forum: General Help
---

### Post by sbarrow on 2008-12-14
I just installed Ubuntu 8.10 on my laptop in a dual boot environment with windows xp. This is the first time I've touched any flavor of linux in 9 years. So far I like it a hell of a lot better than MS. 

If I try to access my works webpage [www.arsmt.com](www.arsmt.com) which is written in asp.net with firefox from ubuntu it tries to load for several minutes then I get: 
Connection Interrupted

The connection to the server was reset while the page was loading.

The network link was interrupted while negotiating a connection. Please try again.


but when I login to windows xp it loads fine. 
I have visited other asp.net webpages and they loaded fine. 

Any Help is greatly appreciated.

Thanks

---

### Post by hikaricore on 2008-12-14
Working fine here.  Might be an internet issue or a dns resolve problem.

Are you using a router?

---

### Post by Izek on 2008-12-14
I get a problem connecting to the site too in Ubuntu 8.04. Though it may be Charter Internet having a problem. I don't know though, never been to the site ever.

---

### Post by sbarrow on 2008-12-14
I am using a wireless router and it is the same wireless router used under my windows xp profile. The site loads fine via XP. How do I do a nslookup from linux? I'm very very new to this platform, but quite confident I will love it once I get comfortable with it.

---

### Post by Izek on 2008-12-14
Install traceroute:
```
sudo apt-get install traceroute
```

then run it
```
sudo tracert www.arsmt.com
```

and see what it gives.

---

### Post by sbarrow on 2008-12-14
Resolves correctly.

---

### Post by SPr on 2008-12-14
I can't access that site either. It doesn't reply to pings though that may be by design. Traceroute comes up with nothing after my ISP's servers.

---

### Post by sbarrow on 2008-12-14
Yeah I have ping replies turned off on our office router.

---

### Post by fubbleskag on 2008-12-14
are you able to browse to other asp pages within linux?

---

### Post by sbarrow on 2008-12-14
I can open microsoft.com. Don't know of any off the top of my head to try.

---

### Post by SPr on 2008-12-14
> **sbarrow said:**
> I can open microsoft.com. Don't know of any off the top of my head to try.

[www.google.com/search?&q=inurl%3A.asp](www.google.com/search?&q=inurl%3A.asp)

---

### Post by sbarrow on 2008-12-14
yeah I can go to other asp pages. Strange. It works fine with IE and FF in the windows environment.

---

### Post by sbarrow on 2008-12-15
Thanks to all for your help. I'll continue to troubleshoot, maybee with older versions of FF. I'm not sure if it is an issue with my office router either. I look forward to freeing my-self from MS.

---

### Post by sbarrow on 2008-12-18
If any of you are still watching this thread, I know kind of know what the problem is. For those of you that couldn't get to it, if you don't mind trying again I would appreciate it.

---

### Post by SPr on 2008-12-20
It works for me now :) Was it a problem with the server?

---

### Post by hivelocitydd on 2008-12-20
As u mentioned you can access other sites with aspx extension , its problem with that site only no probs with ur isp configuration.

---

### Post by dcstar on 2008-12-20
> **sbarrow said:**
> Thanks to all for your help. I'll continue to troubleshoot, maybee with older versions of FF. I'm not sure if it is an issue with my office router either. I look forward to freeing my-self from MS.

It works fine on my 8.04 64-bit system with all the latest patches.

I would suggest you go into your Firefox and delete any cookies for this site, and empty your cache.

---

### Post by louieb on 2008-12-20
> **sbarrow said:**
> ...If I try to access my works webpage [www.arsmt.com]("http://www.arsmt.com") which is written in asp.net with firefox from ubuntu ...I get: Connection Interrupted


Ubuntu Hardy, Firefox 3.0.5 For what its worth - no problem.

---


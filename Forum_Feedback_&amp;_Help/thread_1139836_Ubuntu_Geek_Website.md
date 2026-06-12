---
title: "Ubuntu Geek Website"
date: 2009-04-27
forum: Forum Feedback &amp; Help
---

### Post by gettinoriginal on 2009-04-27
I am not sure where to post this, I did leave a note on his profile but realize he is extremely busy and may not see it for awhile.  I have not been able to access his website for 2 days, I get a failure to load message.  All other websites load fine.  Is this just me, or is his site down?

---

### Post by ubuntu-geek on 2009-04-27
> **gettinoriginal said:**
> I am not sure where to post this, I did leave a note on his profile but realize he is extremely busy and may not see it for awhile.  I have not been able to access his website for 2 days, I get a failure to load message.  All other websites load fine.  Is this just me, or is his site down?
Hi, are you talking about this site? [http://www.ubuntugeek.com/](http://www.ubuntugeek.com/) if so thats not mine :) Perhaps, they are having technical problems?

---

### Post by Elfy on 2009-04-27
ha - I was just about to say that I didn;t think you were that website :)

p s- it was working 5 minutes ago

---

### Post by gettinoriginal on 2009-04-27
Sorry Ubuntu-Geek, that's what I get for assuming #-o.  Thank you and Forest for you quick response.  But I still get "site could not be found"  I am on Firefox, any other suggestions ??

---

### Post by bapoumba on 2009-04-27
> **gettinoriginal said:**
> Sorry Ubuntu-Geek, that's what I get for assuming #-o.  Thank you and Forest for you quick response.  But I still get "site could not be found"  I am on Firefox, any other suggestions ??
Maybe try to clear your cache and cookies?

---

### Post by dmizer on 2009-04-28
Try different DNS servers, and/or disable IPv6.

---

### Post by gettinoriginal on 2009-04-29
How do I disable IPv6?

---

### Post by Kevbert on 2009-04-29
Site seems to be working fine for me. What http error do you get ? Are you using any blocking software such as NoScript ?  How are you accessing the web ? (at college behind a proxy server ?)

---

### Post by gettinoriginal on 2009-04-29
I am hardwired to my ISP modem, and my ISP tech support can access the site, so it is not blocked by them.  I have no blocking applications running.  I can access hotmail, yahoo, craigslist, several https sites.  The only site I cannot access is [http://www.ubuntugeek.com](http://www.ubuntugeek.com).  I get this:
[ATTACH]111663[/ATTACH]  and a few times when clicking links in emails I get a 404 error.  I have changed Firefox config "disable IPv6" to true, but find that Ubuntu 9.04 I would have to recompile the kernel to disable it, and that is way over my head.  I even went so far yesterday to burn a new disk, complete fresh install of 9.04, and the very first thing I did was try to reach ubuntugeek, and still failed.

---

### Post by Kevbert on 2009-04-29
Can you ping [www.ubuntugeek.com](www.ubuntugeek.com) in terminal with
```
ping www.ubuntugeek.com
```
? I believe the IP address is 74.126.24.86 and the site is hosted by a2hosting.com (see if they are blocked).

---

### Post by gettinoriginal on 2009-04-29
I can ping 74.126.24.86, and a2hosting.com both within 40ms
But 
```
ping www.ubuntugeek.com
```  brings back "unknown host"

---

### Post by dmizer on 2009-04-29
Before you try to disable IPv6, I highly reccomend trying different DNS servers. For testing, give Opendns a try according to this howto: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

If that fixes your problem, be sure to follow the steps under "8. NOTE:"

---

### Post by gettinoriginal on 2009-04-29
Thanks for everyones help, but I decided to go back to 8.04,  The more I tinkered with 9.04 the worse things got, and 8.04 works spotlessly from the get go.  :confused:

---

### Post by gettinoriginal on 2009-04-30
Problem solved, I went back to 8.04, then upgraded to 8.10, then to 9.04 and all is working flawlessly, no more Address not found or 404 errors.  Also have sound/video without tinkering.  This makes me very happy, but also confused, as when trying the fresh install of 9.04, I burned 3 disks from 3 different mirrors and got the same problems with each one :confused:  Anyway, problem solved, thanks to you all for your help.

---


---
title: "Failed to Fetch"
date: 2009-04-01
forum: General Help
---

### Post by MGrant on 2009-04-01
First of im new to this so if i need to provide anymore info just let me know

whenever i try to use the synaptic package manager (whether graphical or terminal) i keep getting this response

Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe moto4lin 0.3+svn20071228-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/moto4lin/moto4lin_0.3+svn20071228-1_i386.deb:](http://gb.archive.ubuntu.com/ubuntu/pool/universe/m/moto4lin/moto4lin_0.3+svn20071228-1_i386.deb:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

I use Ubuntu 8.10 Intrepid

thanks for any and all help

---

### Post by Sam Lars on 2009-04-03
Have you always had this problem?
It looks like it's trying to get the updates from your computer instead of the Internet... similar to what it looks like when you add proxy settings to Apt (for apt-cache or something).

---

### Post by MGrant on 2009-04-08
Heya thanks for the info but i just recently fixed the problem. IM still not exactly sure what it was but i had to enter safe mode (or w/e the equivalent of that is in linux) and had to let  Ubuntu fix itself with a little input from me. 
BTW i have seen a lot of posts about this but very few solutions. It literally too me about 3 or 4 hours to figure this one out and it really is quite simple. It wasnt proxy settings though, if i messed with those id be in real trouble since im not even sure how to use them
Thanks for the help though it is very much appreciated

---

### Post by MGrant on 2009-04-08
oh emm...i guess i do need to figure out how to mark this problem as solved though so if you check back here could you explain that to me thanks

---

### Post by Sam Lars on 2009-04-08
When you go to the thread, it's at the top on the right, under Thread Tools.
Thanks.

---


---
title: "hard drive and software configuration"
date: 2006-05-24
forum: Desktop Environments
---

### Post by ynot1270 on 2006-05-24
My first question is:  Why I am only seeing 186 gigabytes of my 200 gigabyte hard drive?  There were no partitions made when formatting, with the exception of the "swap partition" that must be made by default with the Ubuntu version 5.10 (Breezy Badger) software.

My next question is why I am not able to play XM Radio on my desktop pc?  I get an error message saying something about Totem not being able to decode the action of playing XM Radio on my pc.  Would you please tell me what software or application  
needs to be installed to resolve this problem?

---

### Post by htoerrin on 2006-05-24
The answer to the first question is plain mathematics. HD manufacturers define 1K as 1000 while in th PC world 1K is defined as 1024.

200*1000^3 / 1024^3 = 186.26

I don't know anything about XM Radio, but the problem might be that ubuntu does not install al lot of useful codecs by default. Have a look at the tips and tricks section and search for automatix and easyubuntu.

---


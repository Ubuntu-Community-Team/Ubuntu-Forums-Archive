---
title: "Dell Finger print scanner"
date: 2010-03-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamohammed on 2010-03-15
Hello.
Some laptops come with a Finger Print scanner, which is used to log on or accessed password protected anything without actually typing in the passwords.

I've got a Dell Studio 1535. My finger print doesnt work. Can anyone point me in a direction to get it to work on Ubuntu 8.04? (again too lazy to search forum...)

Thank you.

---

### Post by coffeeaddict22 on 2010-03-18
Hi,
Short answer is probably not, almost certainly not in 8.04.  Without a really good reason to be there, 9.10 would be better by far.

Open a terminal, type in ```
lsusb
``` and you'll probably find a line like 
```
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 

```
Which means that like the rest of us you're running an Authentec 2810 fingerprint reader.  The news is not good; [this page on the fprint site]("http://www.reactivated.net/fprint/wiki/Unsupported_devices#AuthenTec_AES2550_.26_AES2810") hasn't been updated in a while, although I read somewhere the 2810 does the encryptation stuff on chip a while back, so someone must have looked.  Bottom line, Authentec don't care.

---


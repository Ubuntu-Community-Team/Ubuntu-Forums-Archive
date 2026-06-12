---
title: "Printing Problem Solved!"
date: 2006-07-04
forum: Desktop Environments
---

### Post by krewemaynard on 2006-07-04
I finally got my Canon i560 working in Dapper! It worked under Breezy with the Pixus drivers, but Dapper printing wasn't happening. 

I finally thought to check my Cups error log, and here's what I found:
```
krewe@76ball:~$ sudo tail -f /var/log/cups/error_log
Password:
E [04/Jul/2006:09:59:48 -0500] cupsdAuthorize: Local authentication certificate not found!
E [04/Jul/2006:09:59:48 -0500] cupsdAuthorize: Local authentication certificate not found!
```
After some other recent trouble with a mail server, I started to wonder whether it was a spooling problem. So, I tried this:
```
krewe@76ball:~$ sudo chmod -R 777 /var/spool/cups
```
I was then able to print again! I don't know if it's just my system or if it's a Dapper problem, but making the Cups spool writeable solved my printing issues. Hope it helps others, Canon users and all. :-D

---

### Post by garba on 2006-07-04
well yes that's a valid workaround but that dir isn't supposed to be world-writable, having to fall back on tricks like that to get printing to work is a pitah, that aythorization problem with cups has been around for way too long imo

---

### Post by mindwarp on 2006-07-07
> **garba said:**
> well yes that's a valid workaround but that dir isn't supposed to be world-writable, having to fall back on tricks like that to get printing to work is a pitah, that aythorization problem with cups has been around for way too long imo

What is the proper solution?

---

### Post by mindwarp on 2006-07-08
I had a similiar message but that message may show up with other messages.  A detailed report on my problems and solution: [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52277/+index](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52277/+index)

---


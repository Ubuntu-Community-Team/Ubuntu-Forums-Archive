---
title: "Connect phone to PC via USB"
date: 2009-06-23
forum: General Help
---

### Post by kauboy on 2009-06-23
Hi,

I've been trying some AT commands of late. When I connected my Sony Ericsson W200i to my PC running Ubuntu 9.04 64-bit using the USB cable that came with the phone, I got *two* "New Mobile Broadband Connection" dialog boxes popping up. I just closed them both and checked my /dev/tty devices listing and shockingly, there were (again) *two* ACM entries, /dev/ttyACM0 and /dev/ttyACM1. Using minicom, I accessed both these device listings separately and when I used the AT+GMM command, they both returned the same device information : Sony Ericsson W200i. I mean, it's as if the same phone has been detected as *two* separate devices. I have no idea why this is happening but it's definitely screwing up my programs which try to handle many phones connected to my PC, sending SMS-es in bulk. This duplication of entries confuses my program into believing there are 2 phones when there's really only one. Is there a way to somehow *remove* /dev/ttyACM1 from the list safely so that the next real phone I connect will take up the name /dev/ttyACM1? I want only /dev/ttyACM0 to be W200i, not another /dev/ttyACM1 too. I couldn't find another appropriate category for this question. Thanks for reading! Hope you have a solution.

Kaushik.

---

### Post by kauboy on 2009-06-23
An update. I deleted the file /dev/ttyACM1, duplicate entry for the SE W200i, and connected another Nokia N79, but it took up the address /dev/ttyACM2 and not /dev/ttyACM1. So I'm still unable to get over the 1 phone 2 addresses problem, deleting the /dev/ttyACM file didn't work. Any help? :(:(

---


---
title: "[SOLVED] WiFi not working on 1525(NOT 1525n)"
date: 2008-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Franc88 on 2008-06-14
Hi all.  I'm a newb to ubuntu and linux in general.  I just got a Dell 1525 laptop, not the 1525n that came pre-installed with ubuntu.  It was actually cheaper to get it with Vista than have ubuntu setup with it(go figure).  Anyways, I've installed 8.04 on a partition of the new laptop but the Wifi adpater is not being recognized by ubuntu.

The wireless adapter is a Dell 1395 802.11g according to the invoice they emailed me.  I just got the thing and would really like to get it to work with ubuntu.  The whole reason I got the laptop was so I can run both OS.

Thanks in advance.

**_UPDATE:_**

I got the wireless adapter to work.  It was recognized by the system but needed to update drivers and install them.  You do need access to wired internet to try what I did.

This thread really help me resolve my issue:  
[http://ubuntuforums.org/showthread.php?t=776626](http://ubuntuforums.org/showthread.php?t=776626)

Although this was not the same laptop model, the steps it discusses proved helpful. With the described steps, I was able to check to see if the adapter is recognized by the system and to find out what chipset the modem uses.  My adapter showed Broadcom too when I did lspci.  Once I determined that, I just followed the rest of the steps that sam_delta suggested.

I hope this helps someone else.

---

### Post by New_Ubie on 2009-01-24
Thanks for taking the time to put the post. I just got my 1525 and installed ubuntu 8.04. i am trying to setup wifi and finding it hard to get the drivers..i did some google and some how i landed in ubutu forums...i checked out your post..i will try that and let you know..

thanks again...

---


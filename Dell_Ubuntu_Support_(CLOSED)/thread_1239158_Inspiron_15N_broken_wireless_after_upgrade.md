---
title: "Inspiron 15N broken wireless after upgrade"
date: 2009-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by donniep152 on 2009-08-13
I have 5 Inspiron 15 N's that are set up with Ubuntu direct from Dell.  After updating their systems approx. 2 weeks ago, 4 out of the 5 systems broke wireless.
I had one of the people contact Dell directly and they reinstalled from the Dell Ubuntu cd but the wireless broke again 40 minutes later.
Right now their not even showing a wireless connection icon.
All 4 are being brought back to me for a "fix" on Friday this week.
I was just wondering if anyone else had this problem and what their fix was before I start digging.

All Inspiron 15N's are running 9.04

Thanks!

---

### Post by coffeeaddict22 on 2009-08-17
Hi,
Depends what they upgraded from.  If it was 8.04 or 8.10, it wouldn't be a surprise; there were a truckload of wireless drivers that got moved into the kernel, and upgrading a previous version broke the wireless.  The problem was that prior to that, most wireless were using ndiswrapper; it keeps it's config file in the ~/home directory, and so when you upgrade the file stays there.  When you boot up after an upgrade, ndiswrapper is still loaded, but so is the Linux driver (you can google the name once you've got your wireless card identified, it's usually something like "wl").

To identify the problem, on a gnome desktop open a terminal and type in ```
nm-tool
```; if that doesn't tell you much, start with ```
ifconfig
``` and ```
lshw -C network
```
Post the output back here if you want/ need more help.

---

### Post by donniep152 on 2009-08-17
Appreciate the response.  We've managed to fix all affected 15n's with a bit of egg on the face of Dell support.

It seems that Dell, in their infinite wisdom changed the Insprion 15n's (1545 series) from using <fn> <F2> to turn wireless on and off to:  <F2> only.  After trying pretty much every option of F2, <ctrl>, <shift>, <alt>, the tech finally found the Dell memo that said they've changed to plain F2.  Once we hit that, it turned on and wireless was back up.
The broken wireless on all machines, as it turned out, coincidentally, was from accidentally hitting F2 and shutting off wireless.


Thanks for helping out.

---

### Post by superm1 on 2009-08-17
There's a setting in the BIOS to control this behavior actually if you want FN-F2 or just F2.

---


---
title: "Partial Upgrade Problems"
date: 2009-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by optimistique1 on 2009-05-09
I just installed 9.04 and in 'software sources' I have ticked all the boxes such as 'proposed updates' etc.

When I ran software update I got a prompt saying 'partial upgrade available'.  I pressed ok and the download screen looked different to the normal software download.  Anyway, I restarted as requested and now the WIFI is not working (Broadcom).  It looks like the update has upgraded the kernel or something...

Anyone any ideas on how to resolve or what I have done wrong.

---

### Post by coffeeaddict22 on 2009-05-09
Hi,
It's almost certainly fixable, but we need a little more info.  Terminal output is easier to post back... what's the output of 
```
lshw -C network
```
```
iwconfig
```and ```
sudo iwlist scan
```
What is/ is not happening?  Does the PC try to connect at all (two whirling dots instead of bars in the network manager icon up on the top panel)?
Finally, were you using ndiswrapper before the upgrade?

---

### Post by ugm6hr on 2009-05-10
Proposed repo can be unstable.

This is a known bub, that looks like there is a fix: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/372876](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/372876)

Don't know when the fix will be released though...

Reboot using the old kernel until then.

---


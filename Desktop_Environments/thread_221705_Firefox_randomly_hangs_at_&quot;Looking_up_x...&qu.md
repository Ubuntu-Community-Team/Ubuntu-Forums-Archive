---
title: "Firefox randomly hangs at &quot;Looking up x...&quot;"
date: 2006-07-23
forum: Desktop Environments
---

### Post by RJARRRPCGP on 2006-07-23
Firefox randomly sits at "Looking up x..." when I go to a web site, even with web sites that I go to everyday! 

It randomly sits at "Looking up x..." for around 20 seconds before the page finally comes up.

This problem occurs even when I disable IPv6. 

The DNS is configured properly.

The problem occurs more often than under Windows! :evil:

---

### Post by invalid on 2006-07-23
> **RJARRRPCGP said:**
> The problem occurs more often than under Windows! :evil:

This suggests that the problem probably actually has little to do with software, if it is occuring in both places.. 

But just for the heck of it, try doing the following when firefox is waiting for a website.```
ping -c 5 <website>
```See if this is able to complete while firefox is still looking it up.

---

### Post by ssodhi on 2006-07-23
Google says "http://www.ubuntuforums.org/archive/index.php/t-7802.html", but that is for 1.0 and a host finding situation. 
Does it say "looking up host"?


Try it out, anyway.

---

### Post by RJARRRPCGP on 2006-07-23
> **ssodhi said:**
> 
Does it say "looking up host"?


It does say "Looking up ubuntuforums.org..." when I want to go over here.

Also, it occurs majorly more often than under Windows. It seems that Linux is having DNS caching problems or even worse, has none!

---

### Post by apollo1900 on 2006-07-23
It seemed that I had basically the same problems with Firefox too! I installed regular Mozilla and that exits as soon as I start it up. My solution? Opera.

---


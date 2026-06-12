---
title: "Unique issue? Boots to Low-Graphics Mode then Freezes"
date: 2012-06-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ozzy1981 on 2012-06-17
I've been doing a few searches around Google and this forum specifically and haven't seen my particular issue.

I bought a Dell i15N-2732BK yesterday and did the quick Ubuntu install through Windows 7.  It worked great.  Super easy.  However it only gave me 20 GB of space on the Ubuntu drive and I couldn't access the other 480 GB of hard drive space so I formatted the HD, booted Ubuntu 12.04(?) from my USB, which I am using now, and reinstalled Ubuntu from the USB.

Now, every time I start up from the hard drive I get the low-graphics mode warning because it doesn't recognize the Intel integrated chip, display, and something else.  I can't remember exactly what it says.  After that the touchpad comes online and I can click ok and get the standard four option page.  But no matter which option I choose, the computer goes out to the command prompt and shows a flashing cursor and does nothing else.

I've tried using

lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print' 

but I don't know anything about using terminal and can't get it to work.

---

### Post by inksterd on 2012-07-07
Hey Ozzy1981, I've got the same issue.  I just started looking for answers, I'll post as I find more info.  Happy hunting!

Update (10:00 PM): You might not like my answer.  I re-booted with my USB flash drive and I looked at a lot of posts, while I re-installed my copy.  The re-install seems to have fixed mine.

You might already have some of these links: 
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) - I like this one because it has a lot of basic techniques that I didn't know about.  Other posts assume that you know how to do some of these things.

---


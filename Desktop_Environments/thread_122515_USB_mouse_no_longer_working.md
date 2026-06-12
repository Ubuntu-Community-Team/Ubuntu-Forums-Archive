---
title: "USB mouse no longer working"
date: 2006-01-27
forum: Desktop Environments
---

### Post by billchivers on 2006-01-27
Hello all,

This is my first post although I have been around a while and I have been using the fantastic Ubuntu since April 2005 (I waited for 5.04). I use Ubuntu on my Toshiba Tecra notebook and Kubuntu on my desktop computer at home (my workplace is, sadly, a Microsoft shop). I have used Linux (previously Mandrake) for over three years, but I would describe myself as a user, rather than a guru.

Which brings me to this post. I installed 5.10 only two weeks ago (installed, rather than upgraded). My USB mouse worked fine, but I was plugging it in after boot-up. Today I accidentally started the machine with the mouse plugged, and it no longer works properly---it does work, but the movement is slow to respond and moves on the screen in a jerky action. The mouse preference settings only help slightly. The curious thing is that the /etc/X11/xorg.conf file has not changed according to its "date modified" in nautilus.

Any ideas?

Thanks,
Bill Chivers

---

### Post by billchivers on 2006-01-27
Mouse problem solved
-----------------------------

I should have added that I tried re-starting the machine with and without the mouse plugged. This did not help.

However, when I powered the machine down completely and then re-started, the problem was solved. I plugged the mouse in when I had the user login screen and it now works.

So what is the difference between re-starting and shutting down? What information is kept during a re-start that is lost when the machine is powered down? Just when I thought I was starting to understand...

Cheers,
Bill Chivers

---


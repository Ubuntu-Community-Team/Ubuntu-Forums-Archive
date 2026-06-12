---
title: "Dell XPS m1330 built-in mic does not work"
date: 2008-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by futuroimperfetto on 2008-08-15
Hello,

I've just bought a Dell XPS m1330 with Gutsy Gibbon preinstalled. Everything seems to work perfectly, for what I have tested, but I cannot get the built-in mic to work. I've downloaded all the avaliable updates, but this did not change the situation. I checked this page

[http://linux.dell.com/wiki/index.php..._Does_Not_Work](http://linux.dell.com/wiki/index.php..._Does_Not_Work)

I downloaded the backport modules and followed the instructions, but when I go to the alsamixer setting, I cannot find digital mic 1, even though I activated the digital input source. I found this page too on launchpad

[https://bugs.launchpad.net/ubuntu/+s...22/+bug/147682](https://bugs.launchpad.net/ubuntu/+s...22/+bug/147682)

There is a comment describing how to download unreleased backport modules. I haven't tried it yet (not even sure if it still is available).

Being a Linux newbie, I'm somewhat hesitant at downloading savagely packages without knowing how to invert the process in case it makes things works.

Does anyone have suggestions about this? I would prefer not to download Ubuntu 8.04 immediately, because my connection is not very good right now. On the other hand, is it known if it is supported on Hardy?

Thanks for your help!

P.S. At first I did not see the Dell Ubuntu support link, so I posted the same question in the absolute beginner's talk. Sorry for the inconvenience.

---

### Post by eggie9001 on 2008-08-17
I am not sure if there would be, but was there a restricted driver for it that was in use, but not enabled? To look at these drivers, go to System -> Administration -> Hardware Drivers. If there is something that relates to your microphone, just enable it*.

*You may need a computer restart to activate the driver.

---

### Post by futuroimperfetto on 2008-09-06
Hi eggie9001,

thanks for your reply :). It appears that the mic is officially supported in Hardy Heron. I noticed this on this page:

[http://blog.higherthings.org/borghardt/article/3633.html]("http://blog.higherthings.org/borghardt/article/3633.html")

and this "official" Ubuntu page:

[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330]("https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330")

I ran a test drive, by trying it on LiveCD first and it was well detected by Ubuntu 8.04. I finally found a good connection and upgraded to Hardy. Everything is now well supported.

However, there is one thing I'd still like to know: how can one raise the volume of the internal mic?

It is rather low, even though all of the levels of the Volume Sound Control and those of "alsamixer" (run in a terminal) are raised to the top.

Am I doing it wrong or should I try something else?

Thanks!

---

### Post by cisoprogressivo on 2008-09-24
Same problem here, the volume of the mic is very low.

---


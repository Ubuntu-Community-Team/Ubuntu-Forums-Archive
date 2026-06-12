---
title: "Ubuntu 9.10 GAMES"
date: 2009-11-01
forum: Gaming &amp; Leisure
---

### Post by KegHead on 2009-11-01
Hi!

I'm trying to find the following deb files:

Pysol

pyramid

these are for 9.10.

Thanks!

KegHead

---

### Post by Vadi on 2009-11-01
Pysol hasn't been updated since 2004 (that's 5 years). Understandable why Ubuntu dropped it... you can still try installing the Jaunty version though, should be fine: [http://packages.ubuntu.com/search?keywords=Pysol&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=Pysol&searchon=names&suite=all&section=all)

---

### Post by mvelte54 on 2009-11-01
> **KegHead said:**
> Hi!

I'm trying to find the following deb files:

Pysol

pyramid

these are for 9.10.

Thanks!

KegHead


I auto-magically assume you have tried Synaptic package manager? 
I found both of these there.

---

### Post by Vadi on 2009-11-01
If you're in Jaunty, yeah... but it got removed for Karmic

---

### Post by KegHead on 2009-11-02
Hi!

Thanks Vadi!!!!

KegHead

---

### Post by funnyname on 2009-11-03
> **Vadi said:**
> Pysol hasn't been updated since 2004 (that's 5 years). Understandable why Ubuntu dropped it... you can still try installing the Jaunty version though, should be fine: [http://packages.ubuntu.com/search?keywords=Pysol&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=Pysol&searchon=names&suite=all&section=all)

Thanks for the input - I will definitely try the older version.

As for not being updated for 5 years - my only thing to that is if it ain't broke don't play with it.  This is the first piece of software I install on all my computers.  It is by far the best solitaire collection out there.  Great variety and user interface.

I was upset to see it disappear from the repository, but if I can install from an older Ubuntu version - just as good.  This is actually the same thing that happen with the Windows version.  Had to hunt hard to find a python and Pysol version that works, now that it is not supported.

---

### Post by octathlon on 2009-11-08
**Hyperventilating**  No Pysol?  :shock:

So what if it hasn't been updated in a long time? Does that make it suddenly broken? Anyone know why they would drop this--the best solitaire game available?

So ... we can install from Jaunty repositories... but that's only available for another year.  Then no more pysol on ubuntu?

---

### Post by hikaricore on 2009-11-09
Perhaps someone should post about this on launchpad.
It may have actually been removed in error or was never packaged for some odd reason.

---

### Post by meborc on 2009-11-09
well, if you save the .deb file, you will have it forever :)

---

### Post by lorddresefer on 2009-11-12
well theres always getdeb.net =)  thats how i got pysol in karmic. I wish it was in the official repositories though...it really is the best solitaire game available

---

### Post by Glucklich on 2009-11-12
> **octathlon said:**
> **Hyperventilating**  No Pysol?  :shock:

I remember there were a couple of Py games with great ideas. Unfortunately, those didn't saw much development and stayed buggy. But solitaire? There are a lot of those out there :s

---

### Post by edlutz on 2009-11-14
> **Glucklich said:**
> I remember there were a couple of Py games with great ideas. Unfortunately, those didn't saw much development and stayed buggy. But solitaire? There are a lot of those out there :s

Yes, but I don't know anything as good as pysol.

IMO, Linux distributions can't afford to drop games for at least two reasons:

1. The number of new GNU/Linux games which become available each time we upgrade the OS is small. Ideally, the number of games directly available from the official repositories should grow as much as possible. This is perhaps THE most important thing to take into account if we want GNU/Linux to become more and more popular. Dropping games works against this purpose. Nobody is commiting changes to that project? So what?!

2. There are people out there which really enjoy a few games and pay little attention to others. For some people that I know, one of those games is PySol (including myself).

KPatience is very cool, but has only a few game types. And the one that I liked the most (Napoleon's tomb) was removed. Not good at all.

Similar decisions happen with other programs too. For instance, one of my daughters still uses Ubuntu 8.04 because she does not want to loose xmms. None of the new options looks as good and simple to use as xmms (specially xmms2, extremely user-unfriendly).

My perception is that we are loosing too much every time we upgrade the system, from programs that disappear to features that we loose (side-effects of tryning to make the system more windows-user-friendly), and new bugs we have to live with.

Nevertheless, Ubuntu is still my favorite distribution and I try to compensate with hard work for features that we are loosing.

---

### Post by marcw on 2010-01-24
I added a bug to launchpad for this.  I'd encourage anyone who wants Pysol returned to the 9.10 repositories to make their feelings known here:
[https://bugs.launchpad.net/ubuntu/+bug/512181](https://bugs.launchpad.net/ubuntu/+bug/512181)

---

### Post by edlutz on 2010-01-25
Thanks, marcw!

After I posted my message, I've found [http://pysolfc.sourceforge.net](http://pysolfc.sourceforge.net), which is an excelent work, BTW! It deserves to be regarded as a continuation and enhancement of PySol.

It would be great being able to install it directly from Ubuntu repositories.

---

### Post by go_beep_yourself on 2010-04-04
No need to run an older version of Ubuntu for software that's no longer in the repositories. Just download the source and compile. Possibly to get Napoleon's tomb in KPatience, is to use an option when running ./configure. See ./configure --help for the available options to compile with KPatience, but if that is not the case, you may need to get the source code of the last version that included  Napoleon's tomb with KPatience and bug the developers a little bit.

What I can't stand about KPatience is that there's no sound when I am playing. Is this because KPatience was made without sound, or is it because I am having a sound issue with KPatience? For similar card games in Windows, they all have sound.

---

### Post by KegHead on 2010-04-04
Hi!

Thanks for the reply!

KegHead

---

### Post by fermulator on 2011-02-20
OH;  Is this the answer?
```
sudo apt-get install pysolfc pysolfc-cardsets
```


It's apparently a fork, but it's in the repositories at least for Ubuntu 10.10.

---

### Post by ladyjack003 on 2011-02-20
f you save the .deb file, you will have it forever

---


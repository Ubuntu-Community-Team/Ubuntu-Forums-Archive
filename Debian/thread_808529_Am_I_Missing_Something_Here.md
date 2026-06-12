---
title: "Am I Missing Something Here?"
date: 2008-05-26
forum: Debian
---

### Post by CJ56 on 2008-05-26
Well, having spent the last year or more with Ubuntu (still my favourite distro) I thought, what is it with Debian? Should I get to know it?

So I put it (Debian Etch) on a spare hard drive. Took a whole day, not because it's inherently too difficult to set up (Envy takes care of the Nvidia drivers, bless it, the rest seems to be pretty much in the repos) but because I kept screwing up xorg.conf trying to get Compiz to work. 

Anyway. I got it all going nicely in the end, nothing very flashy, the basic minimum of internet/word processing/sound & music...but what I seem to have ended up with is just a slightly more old-fashioned-looking version of Ubuntu, with a slightly less feature-rich Compiz. Am I being very dumb here? Is there something I should be doing with Debian that I can't in Ubuntu? Or is it that Debian will keep going week in week out, whereas Ubuntu will topple over in that time? Except that my install of Gutsy (bless it) has worked liked a champ for six months and never shown any signs of temperament.

I'm not trying to be sarcastic or anything: just a genuine inquiry about the merits of this legendary OS.

All comments welcomed... ;)

---

### Post by ibutho on 2008-05-26
The problem seems to be related to the fact that you installed the stable version of Debian. This release does not contain bleeding edge packages at all because its meant to be as stable as possible. If you want the latest and greatest, you should try the testing and unstable branches. Ubuntu is actually based on a snapshot of the unstable branch of Debian. For the xorg.conf issue, you should have backed up your working xorg.conf so that you did not have to reinstall everytime you messed up xorg.conf.

---

### Post by notwen on 2008-05-27
Try Debian Lenny or Sid.  These should have more up-to-date packages that will suit your wants/needs a bit more.  Debian stable releases will always use older packages that have been tried and true for a long period of time.  When Debian insists to be secure and stable, they do so to an extreme, mainly by using packages they know to be secure/stable.

I've ran Debian stable on my file server for almost two years now and have been very pleased w/ Etch since it's release.  Try out Lenny or Sid and let us know if those suit your needs better.  Best of luck.  =]

---

### Post by Raven_Oscar on 2008-05-29
As you probably know there are 3 versions of Debian:
1) stable (Etch now)
2) testing (Lenny). This branch is going to be next stable release of debian.
3) unstable (or just sid).
Dabian stable is used for servers mainly. So it contains soft which is probably not up-to-date but it is well tested and seems to be secure enough to put it in production.   

Ubuntu based on development branches of Debian. So in case if you want to compare Debian and Ubuntu you should install (or upgrade) Debian testing or what is more likely even sid.

---


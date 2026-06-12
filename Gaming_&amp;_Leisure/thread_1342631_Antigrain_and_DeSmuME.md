---
title: "Antigrain and DeSmuME"
date: 2009-12-01
forum: Gaming &amp; Leisure
---

### Post by Zayfox on 2009-12-01
I've been using DeSmuME 0.9.4 until recently, when the 0.9.5 version came out. I was attempting to compile it and it asked me for Antigrain. Okay, I go and download that, but the instructions on how to compile Antigrain are just so awkwardly written I don't understand them.
In short: How am I meant to get this Antigrain library working? I'm running Ubuntu 9.10.

Thanks for any help provided.

---

### Post by Zayfox on 2009-12-01
Solved.
I was compiling the wrong damn library, and I didn't realise I needed libagg-dev.

---

### Post by souldrinker014 on 2009-12-09
Thanks, you have saved me some time.

---

### Post by Axel-P on 2010-02-13
Bumping an old post.

I installed libagg-dev and I still have the "configure: error: Antigrain library is required to build desmume"

Someone knows why?

---

### Post by jv3ga on 2010-02-23
> **Axel-P said:**
> Bumping an old post.

I installed libagg-dev and I still have the "configure: error: Antigrain library is required to build desmume"

Someone knows why?

you must install libagg-dev

apt-get install libagg-dev

;)

---

### Post by Axel-P on 2010-02-24
> **jv3ga said:**
> you must install libagg-dev

apt-get install libagg-dev

;)

I already had it, and the error was still there.

But I have 2 easier solutions:

Repos: [https://launchpad.net/~ronmi/+archive/desmume](https://launchpad.net/~ronmi/+archive/desmume)

Deb: [http://homebrewds.wordpress.com/2009/11/28/desmume-0-95/](http://homebrewds.wordpress.com/2009/11/28/desmume-0-95/)

**------------------------------Update!------------------------------**

[Desmume .96 DEB]("http://homebrewds.wordpress.com/2010/05/19/desmume-0-96/") (you can also try [this link]("http://dl.dropbox.com/u/4376113/desmume_0.9.6-1_amd64.deb"))
 I havent found a PPA for .96 for karmic and/or lynx :( but looks like [it will be there for meerkat]("https://launchpad.net/ubuntu/+source/desmume")

--------------------SOLVED!--------------------

GL HF
Axel

---


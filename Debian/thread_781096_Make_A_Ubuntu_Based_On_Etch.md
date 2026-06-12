---
title: "Make A Ubuntu Based On Etch"
date: 2008-05-04
forum: Debian
---

### Post by tdrusk on 2008-05-04
Basically what I want to do is make my Debian Etch exactly like Ubuntu. I want all the same packages and themes. This is more of an experiment, as I use Ubuntu on my laptop, I want to take my slower computer and make it exactly like Ubuntu.

Any clue how I can do this the fastest way?

---

### Post by dptxp on 2008-05-04
try kanotix, based on debian stable (etch).
i do not know if you can install gnome in kanotix.
check in their forums.
next tune it to look like ubuntu.

---

### Post by ynnhoj on 2008-05-04
> **tdrusk said:**
> Basically what I want to do is make my Debian Etch exactly like Ubuntu. I want all the same packages and themes. This is more of an experiment, as I use Ubuntu on my laptop, I want to take my slower computer and make it exactly like Ubuntu.

Any clue how I can do this the fastest way?
if you want *all* of the same packages, why not simply install ubuntu?  i don't see the point/advantage of tailoring a debian install to be identical to ubuntu.

---

### Post by SunnyRabbiera on 2008-05-04
> **ynnhoj said:**
> if you want *all* of the same packages, why not simply install ubuntu?  i don't see the point/advantage of tailoring a debian install to be identical to ubuntu.

well etch is known for stability, ubuntu is based on sid and sid can live up to its name (see toy story)

---

### Post by jdhore on 2008-05-04
the easiest way (which is a huge cheat, but it works) is to install etch, then run Ubuntu from a liveCD...From the liveCD (it would be easiest if you use Gutsy or possibly Edgy or Feisty), open up a Terminal and run:
```
dpkg --get-selections > packages.txt
```

Then save that file (burn it to a CD or copy it to a flash drive), load up your Etch install, copy packages.txt to your home folder and run:

```
cat packages.txt > dpkg --set-selections
```

once that finishes, finally run:

```
apt-get dselect-upgrade
```

If you get lucky, you'll only have a few package incompatibilities from different package names that Ubuntu uses and packages Ubuntu has but Etch doesn't, but it'll get you as close as you can easily be to a Ubuntu system. Thouse as people in this topic have said, installing all these packages is no better than Running Ubuntu itself, so why do it?

EDIT: Also, if you don't know what cat, dpkg and the > and < signs do, you should not be doing this.

---

### Post by tdrusk on 2008-05-04
> **jdhore said:**
> the easiest way (which is a huge cheat, but it works) is to install etch, then run Ubuntu from a liveCD...From the liveCD (it would be easiest if you use Gutsy or possibly Edgy or Feisty), open up a Terminal and run:
```
dpkg --get-selections > packages.txt
```

Then save that file (burn it to a CD or copy it to a flash drive), load up your Etch install, copy packages.txt to your home folder and run:

```
cat packages.txt > dpkg --set-selections
```

once that finishes, finally run:

```
apt-get dselect-upgrade
```

If you get lucky, you'll only have a few package incompatibilities from different package names that Ubuntu uses and packages Ubuntu has but Etch doesn't, but it'll get you as close as you can easily be to a Ubuntu system. Thouse as people in this topic have said, installing all these packages is no better than Running Ubuntu itself, so why do it?

EDIT: Also, if you don't know what cat, dpkg and the > and < signs do, you should not be doing this.

Thanks.
I'm just doing this for the hell of it. I saw that Linux Mint made a version based on Debian, so I thought it would be cool if there was a Ubuntu that had Debian stability and updates.

After searching around a bit more I found this guide [http://www.debianadmin.com/clone-your-ubuntu-installation.html](http://www.debianadmin.com/clone-your-ubuntu-installation.html) and followed it. The command they suggest is wrong. It should be
```
sudo dpkg --get-selections | grep '[[:space:]]install$'| awk '{print $1}' > packages
```
then I just followed what you except for the install part, where I used 
```
cat installedpackages | xargs sudo aptitude install 
```

I'm sure your commands would have worked, so thanks, but I just used these.

---

### Post by tdrusk on 2008-05-04
Awesome. I had to do some manual labor, but stuff is installing. I will update on how it turns out.

---

### Post by markharding557 on 2008-05-06
why not upgrade to lenny the packages are pretty close for the most part

---

### Post by karellen on 2008-05-07
why not simply use Etch?

---

### Post by tdrusk on 2008-05-07
> **karellen said:**
> why not simply use Etch?
That's what I'm doing now.

I can't believe nobody thinks its a neat idea to make an exact replica just to see the benefits.

---

### Post by ntowakbh on 2008-05-07
> **tdrusk said:**
> That's what I'm doing now.

I can't believe nobody thinks its a neat idea to make an exact replica just to see the benefits.

I can't really see any benefits.  I mean, if your goal is to make an EXACT ubuntu replica...then why not just use the original Ubuntu? I mean, it doesn't really make much sense to me...

---

### Post by tdrusk on 2008-05-07
> **ntowakbh said:**
> I can't really see any benefits.  I mean, if your goal is to make an EXACT ubuntu replica...then why not just use the original Ubuntu? I mean, it doesn't really make much sense to me...
It wouldn't be exact. Just the same programs (different versions). There could be 2 versions, one based on Etch, the other based on Lenny.

When Linux Mint tried this they noticed a lot of advantages.
> This release is an ALPHA release. It is not intented to be used as your main operating system but to give you a technological preview of how Linux Mint would behave if it was based on Debian Testing. 
Debian is a rolling distribution. Compared to Ubuntu, Debian would allow Linux Mint to be faster and to feel snappier and it would ease the process of migrating from one release to another since the Debian base would constantly get updated underneath the Linux Mint desktop.
Debian Testing is unfortunately also less stable than Ubuntu and lacks polish in certain areas.
This experimentation shows us that:
It is possible for Linux Mint to easily switch base (if Ubuntu disappeared or went in a different way)
A Debian Testing base would make Linux Mint faster.
A Debian Testing base would let users transparently go from one release to another by simply applying updates in mintUpdate (release would be like simple snapshots in time)
A Debian Testing base would be easier to maintain in the long term for the Linux Mint dev team
A Debian Testing base would not always be stable, and this would represent temporary problems for both developers and users.
A Debian Testing base would lack the many innovations and improvements developped by the Ubuntu developers, putting more pressure on the Linux Mint team to achieve the same level of polish.
The interesting thing about this experiment will be to see if it still behaves fine in 6 or 12 months time.
In the meantime, you can have a look at it. The ISO acts as a non-installable live CD which you can boot on your computer.

---

### Post by markharding557 on 2008-05-09
what you are talking about here is debian with ubuntu themes and defaults,while you can even install ubuntu binarys into lenny/sid(not etch due to age)it would still be debian with debian repositorys not ubuntu

---

### Post by Erik Trybom on 2008-05-09
I actually think it's a pretty neat idea. All he does is installing the default Ubuntu applications from the Etch repos. Everything's going to be older of course, but in theory it should be more stable too since every package has undergone Debian testing procedures. Or, if we use the Lenny version, we get Ubuntu with rolling release packages.

Of course, if you use Debian you might as well configure the system to your own taste instead of the Ubuntu defaults, but it's very interesting as an experiment.

---

### Post by sujoy on 2008-05-10
not to discourage but etch itself is fast enough on a minimal install, just install whatever you need and its great.

---


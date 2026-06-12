---
title: "How do I upgrade Gimp from 2.2 to 2.4?"
date: 2007-11-16
forum: Dell  Ubuntu Support
---

### Post by RobertGloverJr on 2007-11-16
I have an Inspiron 1420n that came with Ubuntu 7.04 factory installed.  I am reading a book called "Beginning Gimp" published by Apress.  The book uses Gimp 2.4  but the Ubuntu 7.04 on my 1420n is version 2.2.  That version fo Gimp comes standard with 7.04
   I tried to get a new version of Gimp by issuing this command:

sudo apt-get install gimp

    It did some things that made me hopeful that would work.  But when I brought up Gimp it was still version 2.2.

    Suggestions appreciated.

---

### Post by ofb on 2007-11-16
7.10 has GIMP 2.4.0-rc3. Though I admit I'm reluctant to suggest upgrading to 7.10 until more bugs are fixed.

Generally you don't get version upgrades of software with Ubuntu, just bug and security patches. Version upgrades of applications come with each Ubuntu upgrade. This makes dealing with dependencies manageable for the Ubuntu developers.

However there is an exception called Backports
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Gimp isn't listed there yet, and hard to say when or if it will be. Certainly people like to use Gimp, but there may be dependency issues that make backporting 2.4 non-trivial.
[http://packages.ubuntu.com/feisty-backports/graphics/](http://packages.ubuntu.com/feisty-backports/graphics/)

My personal opinion is continue with 2.2 until you're ready to upgrade to 7.10.

---

### Post by inaneframe on 2007-11-16
If you want to upgrade open up "update-manager", it should give you an option to upgrade your distribution, though it does take awhile so pop in a movie and relax or start it before you go to bed.

---

### Post by Dellfan on 2007-11-16
I would tend to agree with ofb regarding upgrading. If everything else works, switching a version for one app seems like a bad plan. Having said that I have 2 machines running 7.04 and one running 7.10, and am having no issues with 7.10. However, I am running it on a standard Dell Ubuntu configured 1505, so there many have been some extra work done to ensure that it would just work.

You need newer version of Pango and GLib to successfully build 2.4 that that might mess up other applications that depend on older versions. If you want to try and just compile it I would suggest reading:

[https://help.ubuntu.com/community/GIMP2.4-on-Feisty]("https://help.ubuntu.com/community/GIMP2.4-on-Feisty")

---

### Post by inaneframe on 2007-11-16
I would never recommend to a person who is new to Linux to compile a piece of software when it is readily available in the latest version Ubuntu.

I have installed 7.10 cleanly on 6 machines without a hitch or a single problem.  I have upgraded 2 machines with 7.04 to 7.10 using "update-manager".

I have an old man that I put 5.10 on his machine originally a almost two years back and I have updated his machine every time with every new release from 5.10 to 6.06 to 6.10 to 7.04 (try doing that with Fedora), I didn't have to this time because he did it himself.  He's 68 and doesn't know the first thing about Windows.  He opened up his update-manager and it asked him if he wanted to upgrade to 7.10 and he agreed.  I go over to his house to visit and he tells me nonchalantly that he upgraded, the only problem that he had was the network manager was messing up a little with his DHCP, I configured it manually for him and everything was alright.  Works GREAT!

Anyway, I think that 7.10 is hands down the best iteration of Ubuntu yet.  A lot of work went into it and I for one am very impressed.

Has there been a lot of problems with it that I don't know about?  I have installed KDE4 and even Enlightenment DR17 on installations without a single problem.  Last I checked 7.10 came out of BETA last month.  :confused:

---

### Post by ofb on 2007-11-16
> **inaneframe said:**
> Has there been a lot of problems with it that I don't know about? 

Yup. Count yourself lucky.
[https://bugs.launchpad.net/ubuntu/gutsy/+bugs](https://bugs.launchpad.net/ubuntu/gutsy/+bugs)
[http://ubuntuforums.org/showthread.php?t=595825](http://ubuntuforums.org/showthread.php?t=595825)

There are always bugs of course, but 7.10 didn't fare as well as the 7.04 release. Give it another month probably to deal with a few bad ones with no workaround.

The business with IDE is particularly nasty. There's a slew of problems (missing devices, burners that read but don't burn, hda & hdb swapping between drives on each boot, etc) that are possibly all related. But whatever it is seems to be up in kernel-land, possibly out of reach of the Ubuntu devs. .23 already has some patches regarding this, and hopefully our .22 will soon follow.

Otherwise I'd suggest upgrading now. It's just the *quality* of some of the current issues have left people with much grief then no option but a full reinstall of 7.04. That's non-trivial for new users of course, so currently I'd encourage anyone happy with 7.04 to stay with it a little longer. We'll see kernel patches for 7.10 soon enough, and much unpleasantness will be behind us.

---

### Post by inaneframe on 2007-11-17
Is it that bad as to warrant a release of an updated install disc?

---

### Post by ofb on 2007-11-17
There's no way I could tell from this end of the use chain.

A decision on revising an iso would hinge on sufficient installation issues to warrant it, as immediately after install the first update can take care of remaining issues. But you'd have to be Canonical to have the required overview to discuss it.

Bad trouble like the IDE isn't an install problem. I'm aware there are installation issues, but I haven't been spending my time on those so don't know how prevalent they are, or how well they've been taken care of with workarounds.

But yeah, an iso could be revised. That's happened. Doesn't really have a bearing on suggesting to wait a bit before upgrading though.

---


---
title: "RPM and DEB"
date: 2008-10-08
forum: Fedora/RedHat and derivatives
---

### Post by HuBaghdadi on 2008-10-08
Hey, 
Usually, my friends and mine are going to a long debate over Ubuntu/Fedora/openSuse
Is it true that the deb packaging system is much more better than the rpm?
My friend told me that rpm could cause many headache while installing packages, something deb doesn't suffer from, true?
Thanks.

---

### Post by neilengineer on 2008-10-08
I don't think so.

I used Fedora which uses RPM from Fedora Core 5, now I am using Ubuntu and Fedora.  I see no big difference between rpm and dpkg(deb).

BTW, that "yum" is slower than "apt-get" if the network speed is the same is true.

---

### Post by RedDwarf on 2008-10-10
> **HuBaghdadi said:**
> Is it true that the deb packaging system is much more better than the rpm?
No.

> **HuBaghdadi said:**
> My friend told me that rpm could cause many headache while installing packages, something deb doesn't suffer from, true?
"could cause many headache while installing packages"? Could you ask your friend to describe this problem in a more abstract way? He can't? Well, then perhaps the first description was too much abstract already.

Ask him for an *specific* problem of RPM not found in DEB and I will say you why he is wrong. And if he starts with something like "Once I tried to..." stop him. Personal experiences are great to explain to your grandchildren, but aren't good descriptions of technical problems.

---

### Post by bwhite82 on 2008-10-12
In my personal experience, its not so much as RPM vs. DEB but rather the front-ends to these. IMO, the front-ends for DEB are far superior. This is why you see many many Fedora/RH users installing Synaptic/Aptitude on their boxes to manage their RPMs.

Edit: I have no experience with Fedora's latest offering: PackageKit (which may work very nicely) I only have experience with Yum, up2date, etc.

---

### Post by gjoellee on 2008-10-12
I think there are more DEB's them RPM's. Also RPM's have caused be a lot of headache when I was using Mandriva. RPM's are just tu unstable if I can say it that way...

---

### Post by RedDwarf on 2008-10-12
> **gjoellee said:**
> RPM's are just tu unstable if I can say it that way...
You can... but it doesn't makes any sense.

If what you mean with "RPMs are just too unstable" is that you had "a lot of headache when you were using Mandriva (that uses RPMs)"... well, your first description was better than the second, there is no need for the later.

---

### Post by HotShotDJ on 2008-10-12
Long, long ago in a galaxy far, far away, RPM (Redhat Package Manager) was, in fact, a pain in the backside.  IF you stuck with official packages from your specific distribution (Redhat, SuSE, Mandrake, etc.) you would usually be OK.  But as soon as you started using software packaged by third-parties, you would almost always enter the nether regions of "Dependency Hell."  For this reason alone, I abandoned RPM based distributions many years ago.  From what I understand, modern distributions that use RPM (Fedora, OpenSUSE, Mandriva) have resolved most of these problems.

While DEB packages are certainly NOT immune to dependency issues, it has historically not suffered from them to the same extent.  I'm not sure if the Debian packaging system simply was more robust, better defined, or if software that does the installing (apt) was just better at resolving dependencies.  Again, I believe that in modern distributions, both RPM & DEB are pretty much on equal footing.

---

### Post by Antman on 2008-10-12
> **hotshotdj said:**
> again, i believe that in modern distributions, both rpm & deb are pretty much on equal footing.
+1

---

### Post by igknighted on 2008-10-13
> **HotShotDJ said:**
> Long, long ago in a galaxy far, far away, RPM (Redhat Package Manager) was, in fact, a pain in the backside.  IF you stuck with official packages from your specific distribution (Redhat, SuSE, Mandrake, etc.) you would usually be OK.  But as soon as you started using software packaged by third-parties, you would almost always enter the nether regions of "Dependency Hell."  For this reason alone, I abandoned RPM based distributions many years ago.  From what I understand, modern distributions that use RPM (Fedora, OpenSUSE, Mandriva) have resolved most of these problems.

While DEB packages are certainly NOT immune to dependency issues, it has historically not suffered from them to the same extent.  I'm not sure if the Debian packaging system simply was more robust, better defined, or if software that does the installing (apt) was just better at resolving dependencies.  Again, I believe that in modern distributions, both RPM & DEB are pretty much on equal footing.

Look at the list of Distro's that you just listed as using RPM.  Three distro's with very different lineage and no real connection to each other aside from the fact that they both use RPM.  Suse grew out of Slackware IIRC, and RPM was added on later to give it a package manager.  Fedora came from Red Hat, and is (in many ways) the originator of RPM.  Mandriva was originally based on Red Hat (about 10 years ago), but they have been diverging ever since and are not too similar.

By contrast, look at the Debian distro's.  Debian itself, then Ubuntu, Mint (essentially Ubuntu), and Mepis.  These distributions are all very close to Debian.  Ubuntu re-syncs to Debian every release, as does Mint, and I think (although cannot confirm) that Mepis uses Debian repo's.

Why does this matter?  When you are using one upstream source, the naming conventions, the packages that each dependency is stored in, and the location in the filesystem where each library should go are going to remain relatively consistent.  When you three independent distributions (the rpm crowd), an RPM for one will very rarely work on the others.

That all said, do people really think that there are more Debs out there than RPM's?  I feel as if every commercial vendor that offers a linux version offers RPMs, and rarely Debs.

---

### Post by seanc7 on 2008-10-14
After having used Fedora Core at my old work for several years and using Debian/Ubuntu at home for more then that, I find "apt-get" much faster then "yum".

I've (so far) never experienced any dependency issues with either DEB or RPM files (ie: Neither package manager installed files, I downloaded from 3rd party's, if they found missing dependencies).

---

### Post by RedDwarf on 2008-10-17
> **HotShotDJ said:**
> Long, long ago in a galaxy far, far away, RPM (Redhat Package Manager) was, in fact, a pain in the backside.  IF you stuck with official packages from your specific distribution (Redhat, SuSE, Mandrake, etc.) you would usually be OK.  But as soon as you started using software packaged by third-parties, you would almost always enter the nether regions of "Dependency Hell."  For this reason alone, I abandoned RPM based distributions many years ago.  From what I understand, modern distributions that use RPM (Fedora, OpenSUSE, Mandriva) have resolved most of these problems.

While DEB packages are certainly NOT immune to dependency issues, it has historically not suffered from them to the same extent.  I'm not sure if the Debian packaging system simply was more robust, better defined, or if software that does the installing (apt) was just better at resolving dependencies.  Again, I believe that in modern distributions, both RPM & DEB are pretty much on equal footing.
Like igknighted explained it's just a question of different distros.

Different distros are well... different. Dont' expect a Fedora RPM to work on openSUSE, or even a Mandriva 2008 RPM to work with Mandriva 2009. Don't five years ago or today. And that applies also to DEB distros.

The differences between Ubuntu 7.10 and 8.04 aren't controlled, and can cause incompatibilities. So, can a DEB package from Ubuntu 7.10 work on 8.04? Yes, can, but you can't be sure.
More differences implies a higher probability of incompatibility. So is more probable that a DEB from 7.10 will work on 8.04 than a DEB from 7.04... but you can only be 100% sure with a DEB built specifically for 8.04.
Obviously the differences between openSUSE and Mandiva are a lot more than the differences between Ubuntu 7.10 and 8.04. So the probability of incompatibility is higher. But everything is a question of probability if you don't use packages for your specific distro version... and I don't want to play lottery with my installed programs.

But this is not a packaging problem. With consistent naming conventions and so you could end with a pretty high *installation* compatibility between RPMs of different distros. But then you have the problem of binary compatibility on Linux. Even if you package your program on a .tar.gz file and install dependencies manually... a subtle ABI break on some library (or more funny things like a symbol being resolved from a different library even if the correct one is loaded in memory) can make your program don't start, start but hang after 10 minutes... or corrupt your data!!

Windows is a consistent platform that made some sacrifices to mantain binary compatibility with old programs, Linux isn't. So never ever expect something built on anything but your specific distro version to work correctly.

---


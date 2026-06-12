---
title: "apt-cacher, apt-mirror or apt-proxy..."
date: 2009-05-19
forum: General Help
---

### Post by expelledboy on 2009-05-19
I am stick of installing via cd. I burnt 4 cd's that where all corrupt, I downloaded 2 iso's on a 64kbs connection, and wiped my server before it decided that the cd was indeed corrupt even after it has passed a cd integrity check! :cry: I even replaced the cd-rom twice to make sure that wasnt the problem.

Eventually to get my server back up and running I booted into a previously working livecd, made a boot partition, installed grub, copied the linux and initrd.gz files from a netboot archive I found somewhere on one of the ubuntu sites and started the install off the net.

So what I want to do once my server finishes installing is set up netbooting using PXE. The client will boot off the network and start installing. The thing is I want a cache of all the packages it requests from the internet so when the next client needs to be setup most (if not all) of the package are on my side of the slow connection.

I found three packages that look like they might do the job but am unsure as to which is best for my purpose.

I want it to cache all the packages I download from the repos, remove the older packages that have since been updated, work for all ubuntu releases and architectures, and client configuration should be as minimal as possible. I also want to be able to point my netboot installer to it..

So which, apt-cacher apt-proxy or apt-mirror, should I use?

What are the differences between them? Which does ubuntu recommend?

Ah... my install has reached 83%! Its going to be a all nighter.. :popcorn:

---

### Post by cariboo on 2009-05-19
Have a look at this wiki [page]("http://help.ubuntu.com/community/UbuntuLTSP"), it should help you setup what you need.

---

### Post by expelledboy on 2009-05-24
> **cariboo907 said:**
> Have a look at this wiki [page]("http://help.ubuntu.com/community/UbuntuLTSP"), it should help you setup what you need.

Thanx. Will look through it..

---

### Post by AlexanderDGreat on 2009-12-23
This if an article for human beings about APT-mirror and APT-cache:

[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher]("http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher")

Hope it helps.

PS I gave up on LTSP because it's too slow for my standards versus workstations with hard disks, but controlled apps, settings, security, etc...

---


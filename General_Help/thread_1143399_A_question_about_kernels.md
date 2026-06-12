---
title: "A question about kernels"
date: 2009-04-29
forum: General Help
---

### Post by cubical10 on 2009-04-29
I am not sure where to post this, but...

I have a question about kernels.
On my recently purchased Asus eeePc 1000HE I installed 9.04 release candidate.  Now that 9.04 is released I am about to install it again.

When I first installed the RC, I ran into some issues.  A suggestion, was to install kernel 2.6.29.  So I did, and I did notice improvements with the Wifi and battery life.
I used the .debs from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).

Now I see that the release kernel for Jaunty is 2.6.28.  I believe that this will be the only supported kernel for the life of Jaunty.
I believe that Karma will be released with 2.6.30.
So what is it about 2.6.29 that it gets skipped? 

I know that when I reinstall with Jaunty final I can simply install the .debs for kernel 2.6.29.x.  But, I guess my question how are kernels selected for a release?  And are there any ramifications from running the non standard kernel?

---

### Post by mb_webguy on 2009-04-29
Kernels aren't locked in like normal software.  When a new kernel has been released and thoroughly tested, it will be added to the repositories.  Update Manager will consider this a security update, so will notify you within a day of the release.

Edit: eldragon is right.  I misread the OP, and for some reason thought you were talking about subversions (e.g. 2.6.28-**11**).

---

### Post by eldragon on 2009-04-29
this is how the ubuntu release cycle works.

once an OS version (jaunty) hits the feature freeze date, no new versions of software are added...just security updates.

when jauny got feature frozen, the latest kernel was .28 so there you go.

if you have the RC installed already, just apt-get update and apt-get upgrade and you will be set, no need to reinstall

---

### Post by cubical10 on 2009-04-30
So why is kernel 2.6.29 being skipped?

Why is there a kernel team working on 2.6.29, if as it appears that 9.10 will use kernel 2.6.30.x?

Are there any reasons that I should not use kernel 2.6.29.x?


> **eldragon said:**
> if you have the RC installed already, just apt-get update and apt-get upgrade and you will be set, no need to reinstall

I know, but I have always re-installed from scratch when moving from a beta/rc to the full release.  I had some sound issue when going from 8.04 beta thru rc to release that were only fixed by a fresh install.

---

### Post by my_key on 2009-05-07
Uneven release numbers are for development versions or tests. See: [http://beta.selfplatform.eu/viewL?ssid=7380&cssid=7224](http://beta.selfplatform.eu/viewL?ssid=7380&cssid=7224) (and do a page search for "uneven release").

Ciao
m

---


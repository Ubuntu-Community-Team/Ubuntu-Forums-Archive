---
title: "Can't Install AWN"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by impulse29 on 2008-01-13
When I try to install AWN, I get the following error:

The following packages have unmet dependencies:
avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not going to be installed
awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
Depends: libawn-bzr but it is not going to be installed
Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

I can't install any of the dependencies without the libpango, and the version that is on synaptic is too old. Any thoughts? Is there another repository I could add that has the new version of libpango on it?  I've searched, and there are a few with the same problem, but nobody has been able to give an answer (without linking to a 60 page thread). 

Any help is appreciated!

---

### Post by Tenken on 2008-01-13
Which AWN repository are you using? I installed AWN (on Gutsy) just fine with the repo found on [AWN wiki]("http://wiki.awn-project.org/index.php?title=DistributionGuides").

---

### Post by impulse29 on 2008-01-13
I used the repository found on their site: 
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

I don't understand how some people can install it, when it requires a newer version of libpango than ubuntu uses?

Are there any repositories with a newer libpango? I know the newer version exists, and I've tried installing it, but synaptic still only sees the old version. I can't uninstall the old version either because it has toooo many dependencies.

---

### Post by Tenken on 2008-01-13
Did you update your repositories since you added the AWN one? If not type this in the terminal

```
sudo apt-get update
```

That should update the package listing for all installed repos.

---

### Post by impulse29 on 2008-01-13
Yes, I followed all the instructions on the page and still nothing.

What version of libpango does it say is available in synaptic? 

I might just reinstall ubuntu, but I'd rather get it to work.

---

### Post by Tenken on 2008-01-13
I'm not on my comp with AWN, but this one also runs Gutsy and has libpango1.0.0, libpango1.0.0-common and libpango1.0.0-ruby

---

### Post by g0vP on 2008-01-23
Uhm I've been having the same prob for a while, but after some tinckering with synaptic settings, I managed. What I did was:

Settings>Repositories>Third Party Software tab
Maker sure that "http://download.tuxfamily.org/syzygy42" and "http://download.tuxfamily.org/syzygy42" are added, then make sure them, as well as the original 2 are ticked

then

Updates tab
Make sure "Important" & "Recommended" updates are ticked.

Then try again, it worked for me!

Good luck

---

### Post by tripitaka on 2008-02-04
The above steps worked for me, thanks!

---


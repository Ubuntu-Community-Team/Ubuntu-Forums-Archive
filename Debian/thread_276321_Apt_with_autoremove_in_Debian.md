---
title: "Apt with autoremove in Debian?"
date: 2006-10-12
forum: Debian
---

### Post by VFiend on 2006-10-12
The version of apt in Edgy basically does the same thing as aptitude - keeps track of which packages are manually installed and which were installed as dependencies to removed packages that can be safely uninstalled. It's good for minimizing cruft and unneeded packages.

So I'm curious because I can't find any information on this and people using Debian should know - has this been implemented in Debian yet?

---

### Post by richbarna on 2006-10-15
I am using Debian Etch, and apt is just apt it doesn't keep track of dependencies. Aptitude does however. 

Are you saying that in Edgy apt does the same as aptitude but is called apt? Sorry, I don't use Ubuntu and am wondering why you wouldn't just use aptitude.

This sounds strange to me. 

Are you saying that you could do an "apt-get install kubuntu-desktop" then later an "apt-get remove kubuntu-desktop", and it would remove all the dependencies and packages just the same as aptitude?

I've been away from Ubuntu for a while but I've not heard about apt having these capabilities, nor on Debian.

---

### Post by VFiend on 2006-10-15
> **richbarna said:**
> Are you saying that you could do an "apt-get install kubuntu-desktop" then later an "apt-get remove kubuntu-desktop", and it would remove all the dependencies and packages just the same as aptitude?

Yes, something like that, it's also implemented nicely in Synaptic so you don't always have to use aptitude. Anyway, thanks, just curious.

---

### Post by shining on 2006-10-26
I believe this was in experimental, but I don't know if it still is. In any cases, I believe the developer who added this feature didn't have time to also maintain debian packages, so he mostly concentrated on ubuntu ones.
Note that this feature isn't for free, more work needs to be done when installing/removing packages, so there can be a performance impact.

---


---
title: "Can I obtain the deb files for packages included in the distro?"
date: 2009-05-13
forum: General Help
---

### Post by Buttons840 on 2009-05-13
Example:  I just installed Jaunty.  The fresh install has 1100+ packages install according to synaptic, yet there is not a single deb file in the cache or CD*.  (Not that I can find anyways.)

Is there a way to obtain these deb files?

I know I could download packages only from synaptic, but is there a way to obtain the deb files included with the new distro without downloading them?

*When I say no deb files in cache or CD, what I mean is very few debs.  I know there are a couple debs, but not the ones I'm looking for.

Thanks.

---

### Post by Tipped OuT on 2009-05-13
I'm not surprised that there aren't a lot of .deb's in the CD. Have you ever seen a Windows Installation CD/DVD with a lot of .exe's? I believe it's for security reasons, they archive them in some special format, then the installation extracts and installs them.

---

### Post by Cheesemill on 2009-05-13
> **Tipped OuT said:**
> I'm not surprised that there aren't a lot of .deb's in the CD. Have you ever seen a Windows Installation CD/DVD with a lot of .exe's? I believe it's for security reasons, they archive them in some special format, then the installation extracts and installs them.

This just isn't true.

The LiveCD doesn't have any .deb packages because it contains a squashed filesystem of an installed version of Ubuntu that gets decompressed onto your drive when you install, the packages don't get installed one by one.

If you look at the alternate install CD then it contains all of the .deb packages that you would expect, there just isn't room on 1 CD for the squashed filesystem (which is what enables the live CD to work) and the packages.

This is also the reason why you can only perform an upgrade from the alternate CD and not the live one

To get all of the default packages you could just download the alternate CD.

Cheesemill

---

### Post by Yellow Pasque on 2009-05-13
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Tipped OuT on 2009-05-13
> **Cheesemill said:**
> This just isn't true.

The LiveCD doesn't have any .deb packages because it contains a squashed filesystem of an installed version of Ubuntu that gets decompressed onto your drive when you install, the packages don't get installed one by one.

If you look at the alternate install CD then it contains all of the .deb packages that you would expect, there just isn't room on 1 CD for the squashed filesystem (which is what enables the live CD to work) and the packages.

This is also the reason why you can only perform an upgrade from the alternate CD and not the live one

To get all of the default packages you could just download the alternate CD.

Cheesemill

I was mostly speaking through my Windows experience and knowledge, thought they where similar. Thanks for clearing things up. ;)

---


---
title: "gnome 3.28 on Ubuntu Mate 16.04"
date: 2019-07-31
forum: Desktop Environments
---

### Post by adel.ejjeh on 2019-07-31
Hello all!

I am running Ubuntu Mate 16.04 and I wanted to get the gnome-3 desktop environment. First I tried to install it using apt but realized that I got version 3.18.5. I then saw that I can get version 3.28 using the snap store, so I installed that. However, my default gnome applications are still running the 3.18 version. Is there something I can do to point the system to the updated gnome version that I installed using snapd? I was thinking of just uninstalling the apt version but wasn't sure if that would break something in the system so I wanted to check with them community first :)

Thanks!

---

### Post by Dennis N on 2019-07-31
You have to use the version that works with the Ubuntu core components on your system. That's the version in the Ubuntu repository. Besides that, I don't see any gnome-desktop package in the snap store. There is Gnome 3.28 Runtime, but that is not the same as gnome-desktop. 

If you want the best experience with gnome desktop, you should install Ubuntu 18.04, or install Ubuntu 18.04 in a virtual machine.

---

### Post by cruzer001 on 2019-07-31
Mate LTS releases are supported for three years, which means your running a version that has reached end of life and no longer supported.  Only Ubuntu-gnome has 5 (10/paid version) years of support.

Time to upgrade to 18.04

---

### Post by Dennis N on 2019-07-31
> Mate LTS releases are supported for three years, which means your running a version that has reached end of life and no longer supported.

We should say "no longer fully supported". In fact, most packages (over 80%) are supported until 2021. I ran this on Ubuntu MATE 16.04:

```
dmn@Sydney:~$ ubuntu-support-status
Support status summary of 'Sydney':

You have 59 packages (3.1%) supported until April 2021 (Community - 5y)
You have 1475 packages (77.2%) supported until April 2021 (Canonical - 5y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 376 packages (19.7%) that are unsupported

```

So 20% unsupported. And many of those are mate-specific packages (like mate-panel, mate power manager, mate-control-center, etc). Question is, will these have security risks? I choose to continue using mine.

---

### Post by cruzer001 on 2019-07-31
Hi Dennis

I may be wrong, but that support-status does not add up to 100% support and U-desktop would.  And saying not fully supported creates the image of bullet holes in my mind.

[https://ubuntu-mate.community/t/ubuntu-mate-16-04-lts-reaches-end-of-life/19425](https://ubuntu-mate.community/t/ubuntu-mate-16-04-lts-reaches-end-of-life/19425)

---

### Post by Dennis N on 2019-07-31
> that support-status does not add up to 100% support
But it does: 3.1% + 77.2% + 19.7% = 100%

Included in this, the kernel continues to be supported, and so does Firefox. I don't have statistics, but I think most security risks would occur in these, and in the user's own bad habits.

If the OP is concerned, by all means upgrade. 

And consider: there may be as-yet unknown security risks that could be exploited right now in Ubuntu 18.04. What are the chances? Not zero. Yet, we don't stop using it.

---

### Post by adel.ejjeh on 2019-07-31
Thanks for the feedback! The main reason I wanted to move to a newer version was because I wanted the "dock" on the left that appears in Ubuntu 18.04. Unfortunately I cannot move this machine to 18.04 because it is a research machine and I use some software on it that does not support newer Ubuntu versions.

---

### Post by cruzer001 on 2019-07-31
Thats a whole different thing than installing gnome3 on a gnome2 system :)

I think you should just install a dock or another panel, something I do not use.  Others will have suggestions.

@Dennis
100% of base packages?
> If you're still running 16.04 LTS and are not ready to upgrade, don't panic! Your system will still be as secure as the Ubuntu base until April 2021, but please bear in mind some of your packages and applications will no longer receive updates.

Just seems like not a good practice to me.

---


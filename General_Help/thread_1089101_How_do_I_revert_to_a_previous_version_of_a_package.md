---
title: "How do I revert to a previous version of a package with synaptic?"
date: 2009-03-06
forum: General Help
---

### Post by UbuJules440 on 2009-03-06
Long story short,

There are some issues with my bleeding edge graphics card that I thought might be solved with the new intel driver from [http://ppa.launchpad.net/xorg-edgers/](http://ppa.launchpad.net/xorg-edgers/), so I added them to my sources list, updated and the software update application showed the bleeding edge drivers, as well as libdrm, mesa, dri, xserver, etc. - about 10 packages in all.

I upgraded, rebooted, tested, didn't like the performance and want to go back to the previously installed versions (some from the intrepid CD, some from updates afterwards).

I've read that you can Package > Force a version with Synaptic. That would seem to work with xserver-xorg-video-intel, for example, but when I try the same thing with libdrm2 (also installed from the ppas as above) it also flags compiz, fspot, gdm, xbmc, etc. to be removed.

Is there a simple way to revert just the packages installed from the ppas to the previous version without touching the rest of the system?

---

### Post by dcstar on 2009-03-06
> **UbuJules440 said:**
> Long story short,

There are some issues with my bleeding edge graphics card that I thought might be solved with the new intel driver from [http://ppa.launchpad.net/xorg-edgers/](http://ppa.launchpad.net/xorg-edgers/), so I added them to my sources list, updated and the software update application showed the bleeding edge drivers, as well as libdrm, mesa, dri, xserver, etc. - about 10 packages in all.

I upgraded, rebooted, tested, didn't like the performance and want to go back to the previously installed versions (some from the intrepid CD, some from updates afterwards).

I've read that you can Package > Force a version with Synaptic. That would seem to work with xserver-xorg-video-intel, for example, but when I try the same thing with libdrm2 (also installed from the ppas as above) it also flags compiz, fspot, gdm, xbmc, etc. to be removed.

Is there a simple way to revert just the packages installed from the ppas to the previous version without touching the rest of the system?

Any previous version must exist in a repository for you to use "Force Version", otherwise you need the actual .deb package on you system so you can install that manually.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) has all available official packages that you can download manually.

---

### Post by UbuJules440 on 2009-03-06
> Any previous version must exist in a repository for you to use "Force Version", otherwise you need the actual .deb package on you system so you can install that manually.

Yep. They're in the repository, I can see the old versions when I use "Force Version".

The problem is that if I do this for xserver-xorg-video-intel - everything's fine and synaptic shows me the old version.

If I do it for libdrm2 (for example), I get a window that says "Mark additional required changes?" and under "To be removed" I see compiz, compiz-core, etc, xbmc, gdm, gnome-screensaver - just to name a few - that weren't installed with the bleeding edge versions. Why is synaptic asking me to remove those?

---

### Post by dcstar on 2009-03-06
> **UbuJules440 said:**
> Yep. They're in the repository, I can see the old versions when I use "Force Version".

The problem is that if I do this for xserver-xorg-video-intel - everything's fine and synaptic shows me the old version.

If I do it for libdrm2 (for example), I get a window that says "Mark additional required changes?" and under "To be removed" I see compiz, compiz-core, etc, xbmc, gdm, gnome-screensaver - just to name a few - that weren't installed with the bleeding edge versions. Why is synaptic asking me to remove those?

Probably because those packages depend on the particular library package(s) you are trying to downgrade, and since a downgrade means a removal first that message appears.

You can allow it to remove them and then reinstall them all later (assuming you system still works.....), but it can be tricky.

If you are concerned about "forgetting" any particular package, you can save your list of installed packages with "Edit-Save Markings" and then reload that list later.

You may want to manually download that package you want and try an install of it.

---

### Post by UbuJules440 on 2009-03-07
Thanks for your tips.

I figured out that if I "forced" all of the other packages to a previous version first, when I got to libdrm2 it didn't want to remove the stuff it wanted to remove before.

---

### Post by dcstar on 2009-03-07
> **UbuJules440 said:**
> Thanks for your tips.

I figured out that if I "forced" all of the other packages to a previous version first, when I got to libdrm2 it didn't want to remove the stuff it wanted to remove before.

Now you know why some people dislike "upgrades" just for the sake of it - the roll-back can be a real pain!

I have backports turned off in my 8.04 system because some of the backported 8.10 packages bring a major mouse bug with them, and there were so many packages to roll back the easiest solution was a fresh 8.04 install.

I still use some bug-fixed backported packages, but I manually download and install them rather than using the backports repository.

---


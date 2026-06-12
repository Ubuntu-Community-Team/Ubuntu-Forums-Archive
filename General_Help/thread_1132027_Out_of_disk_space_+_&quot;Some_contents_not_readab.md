---
title: "Out of disk space + &quot;Some contents not readable&quot; in /var"
date: 2009-04-21
forum: General Help
---

### Post by qyot27 on 2009-04-21
As the title says, I've recently hit this major snag.

The background:
I was wanting to set up a cross-compilation environment with MinGW so that I wouldn't have to go to the trouble of setting it up in Windows.  The problem was/is, the version of MinGW in the repos is not adequate for cross-compiling ffmpeg, because it needs a newer version of the MinGW runtime.

So, following a post in one of the threads around here, I found this site, which offers a Makefile that will facilitate downloading, compiling, and installing an up-to-date MinGW environment:
[http://www.profv.de/mingw_cross_env/](http://www.profv.de/mingw_cross_env/)

That would have been fine, but I could not find anything on that site over how much space would be taken up by this.  During one part of the compiling stage, my disk space ran out (I'd watched it drop from ~196-+200MB to 160MB to 96MB to finally when it utterly failed).

After it failed, I resigned myself to just setting up MinGW properly under Windows, so I deleted the working folder all the stuff was being downloaded to and all, to see if that would free up the disk space.  No dice.  Nor could I seem to find any tmp remnants of the files (nothing in /tmp or /var/tmp worth mentioning).  Oddly, /dev reports that there's 121MB of free space, but all other folders I've checked report 0.  This doesn't change no matter if I'm root or not.  Additionally, all my bookmarks in Nautilus and Firefox are now gone (although this could be due to me attempting to clear up space and unknowingly deleting them).  Going into Synaptic and removing programs either doesn't work at all or doesn't affect the disk space if it does.

If I try to look at the properties for /var, it reports "(some contents not readable)", which I've seen referenced as being indicative of filesystem corruption.

My question is: is there any way to recover that free space without wiping the partition and reinstalling?  With 9.04 only a couple days away I've considered it, but I'd like to avoid doing a complete reinstall if I could - I'd rather not have to go through the hassle of customizing everything to my liking again.  Unless there's a *really* simple way of preserving *all* my user settings (installed apps/themes, menus, backgrounds, etc.) separately and reapplying them later.

---

### Post by NT4usB on 2009-04-21
Boot to the Ubuntu live CD. Then you can check the drive integrity.
Also, look at removing old kernels, /var/log files, etc. to free up space.
You can also steal some space from adjacent partitions using gparted live CD. Swap is a good candidate if it's next door.

---

### Post by qyot27 on 2009-04-21
I always uninstall old kernels through Synaptic any time I notice a change in GRUB (unless that's not what you mean), and I can't remember if I did anything with /var/log.  I also have Synaptic set to not cache downloaded packages.

Unfortunately, I can't take any more space for the system partition - it'd run past the 137GB barrier and become unbootable.

---

### Post by NT4usB on 2009-04-22
I have a peek in /boot and look for stale kernels, kernel...bkup, etc.
Don't know why but always seems to be one with a .bkup on it, not doing anything but taking up space.
It's not a lot but for me, the difference between upgrading or not.
...I have a couple boxes I built in the early days I didn't make /boot large enough so two kernels and a bkup and it's plugged.

---


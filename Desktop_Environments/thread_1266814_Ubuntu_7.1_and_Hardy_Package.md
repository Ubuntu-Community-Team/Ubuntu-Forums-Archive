---
title: "Ubuntu 7.1 and Hardy Package"
date: 2009-09-15
forum: Desktop Environments
---

### Post by Mr.Jkate on 2009-09-15
I installed 7.1 last year. sources.list files has urls to gusty packages. I build my application and deployed. 
Yesterday I installled ubuntu7.1 and tried to setup development environment but found that gusty packages more available. So I took sources.list from 8.1 has has urls to hardy packages..so I install hardy packages using apt-get build-dep gnome-panel, firefox etc.. and compiled my application and deployed. But is it handing after 20 to 30 minutes.. 
Can this be problem of hardy packages... ? if yes... is there any way I can get gusty packages...

Please advise.

-James.

---

### Post by dawynn on 2009-09-15
OK, I'm trying to follow here.

You may want to review this wikipedia article ...
[http://en.wikipedia.org/wiki/Ubuntu_releases](http://en.wikipedia.org/wiki/Ubuntu_releases)

Note, we use .10, not .1.  Unlike math class, these are not equivalent (its the difference between "January" and "October")

Also, as you can see in the wikipedia article -- Gutsy (7.10) has seen the end of its lifecycle.  You could, potentially, get it working, or reinstall from CD, but very likely will not find the proper security updates.  You actually do want to move to Hardy at the bare minimum -- its the current Long-Term Support release.  But Hardy was 8.04, not 8.10.

If you have repositories that use the version number as part of their url, then make sure that you are in-synch with your other repositories.  For instance, Crunchbang Linux uses the version number.  So, if you are using 8.10 libraries, use "intrepid" as the version for your other repositories -- mixing releases can get ugly fast.

Granted, an upgrade from one version to another can take a considerable amount of time -- especially dependent on your download time, and the repository mirror you've chosen.

Once you've chosen a particular release (as of this date, I would recommend either Hardy (8.04) for LTS, or the latest stable release -- Jaunty (9.04)), update your /etc/apt/sources.list so all repositories are consistent with that release.  (You'll also want to review the files in the sub-directories there -- I think its /etc/apt/sources.list.d) Then make sure all of your chosen packages are up to date.  Synaptic, aptitude, or any package manager can help with this.

Here is helpful documentation on moving from Gutsy (7.10) to Hardy (8.04):
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

Once your system is current on a supported release -- then you should be ready to start testing your package.  Yes, like other OS's, we drop support for old releases (Microsoft no longer supports Win 3, '95, ME, etc), but with Ubuntu, the upgrades are free.  If your internet connection is slow, we're even willing to send an install disk.
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

---

### Post by snowpine on 2009-09-15
> **Mr.Jkate said:**
> I installed 7.1 last year. sources.list files has urls to gusty packages. I build my application and deployed. 
Yesterday I installled ubuntu7.1 and tried to setup development environment but found that gusty packages more available. So I took sources.list from 8.1 has has urls to hardy packages..so I install hardy packages using apt-get build-dep gnome-panel, firefox etc.. and compiled my application and deployed. But is it handing after 20 to 30 minutes.. 
Can this be problem of hardy packages... ? if yes... is there any way I can get gusty packages...

Please advise.

-James.

Hi James, you can't mix and match between releases (gutsy/hardy/intrepid etc.) and gutsy is no longer supported.

Since you mention this is a brand-new install, I recommend simply doing a fresh reinstall of the current version (9.04 jaunty).  Good luck!

---

### Post by KentonS on 2009-09-15
> **dawynn said:**
> Here is helpful documentation on moving from Gutsy (7.10) to Hardy (8.04):
[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

Is the recommended Network Upgrade from 7.10 to 8.04 still available? I've read in these forums and elsewhere that it may not be. I'd just go ahead and try it, but I'd hate for it to fail somewhere in the middle and leave me with an unusable system.

I hesitate to just do a cold install, because I'm using 7.10 on a laptop, and I've heard from multiple sources that, basically, all bets are off when it comes to laptops. Desktops are OK, but laptops not so much. At least with an upgrade install, there's a better chance that functionality implemented via various configuration files and scripts that make the whole thing work on the laptop *may* be preserved. Or not.

I'm a pretty technical-type guy, but I'm new enough to the Linux environment to be very afraid.

Thanks!

---

### Post by snowpine on 2009-09-15
> **KentonS said:**
> I hesitate to just do a cold install, because I'm using 7.10 on a laptop, and I've heard from multiple sources that, basically, all bets are off when it comes to laptops. Desktops are OK, but laptops not so much. At least with an upgrade install, there's a better chance that functionality implemented via various configuration files and scripts that make the whole thing work on the laptop *may* be preserved. Or not.


I recommend burning a couple of Live CDs (8.04 and 9.04). If the Live CD works on your hardware, it is safe to install.

In my experience, each release gets progressively better at hardware recognition as support for more devices is added to the kernel.

---

### Post by KentonS on 2009-09-15
> **snowpine said:**
> I recommend burning a couple of Live CDs (8.04 and 9.04). If the Live CD works on your hardware, it is safe to install.

In my experience, each release gets progressively better at hardware recognition as support for more devices is added to the kernel.

Hi, snowpine.

That's pretty much what you said in another of my threads related to this subject - at [url]http://ubuntuforums.org/showthread.php?t=1258966. Unfortunately, though, neither response really answers my question. They suggest an alternative, but they don't answer the question.

Thanks for your input though!

---

### Post by snowpine on 2009-09-15
> **KentonS said:**
> That's pretty much what you said in another of my threads related to this subject - at [url]http://ubuntuforums.org/showthread.php?t=1258966. Unfortunately, though, neither response really answers my question. They suggest an alternative, but they don't answer the question.

If I understand the question, it's "will Ubuntu 8.04 work OK on my laptop?"

Trying the Live CD is the quickest and easiest way to answer that question.

In my opinion, 9.04 (the current version) has ever better hardware support than 8.04, so that's worth a try as well.

---

### Post by dawynn on 2009-09-15
In my experience, the couple times that I've tried to use the automated install, 
a) Something goes wrong in the middle, and it doesn't work out to be truly automatic,
b) Certain things get removed or added, and I have to go and sort out in the end anyway

Typically, I do my upgrades more or less "by hand".  I use aptitude.  I mark about 100mb or so of packages for upgrade, fix any broken dependencies, make sure that I approve of what aptitude will do, and approve the upgrade.

It's more time consuming in the long run, but my system stays with the packages I like.  And because of the apt packaging system, I can typically stop upgrading in the middle and *generally* not have anything too badly broken.  Sometimes it takes a few logins to get this method to work, but it does work.

Such a method will work for upgrading, even if the Gutsy repositories are no longer available.  In fact, if you can figure out a few dropped dependencies where package names have radically changed, such a method should work for "skip" upgrades -- say moving from Gutsy directly to Jaunty.  But that's for the truly courageous.

Then again, I'm just beginning my experiences in the laptop world...

---

### Post by slakkie on 2009-09-15
You can use old-releases.ubuntu.com in stead of archive.ubuntu.com for installing/updating 7.10 packages. Doing network upgrades is also possible, see [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by slakkie on 2009-09-15
> **dawynn said:**
> 
Note, we use .10, not .1.  Unlike math class, these are not equivalent (its the difference between "January" and "October")


Jan would be 01, not 1 in the ubuntu version convention.

---

### Post by steveneddy on 2009-09-15
Perform a fresh install. Versions of Ubuntu prior to 8.04 are no longer supported officially.

8.04 Hardy is a Long Term Support version supported for many more years.

8.10 Intrepid is supported for about a year more.

Further versions are only supported for six months and can be "buggy".

Personally I recommend Hardy or Intrepid for a more "stable" version of Ubuntu.

There is another LTS coming in April which should be a great Ubuntu release.

Good luck.

---

### Post by KentonS on 2009-09-15
Thanks very much for the responses, folks!

snowpine: Actually, my question in the other thread was "Given the stripped-in list of installed devices on my laptop, does anyone see any potential problems of which I should be aware?" I was hoping that if there were, someone would be able to point me to resources I would need to resolve those problems, so I could anticipate them and have a possible solution in hand before starting the upgrade.

dawynn: Your process sounds much more involved than anything I'm prepared to tackle.

steveneddy: Funnily enough, I spent the entire time between my last post and this one reading the ***outstanding*** information at the "Ubuntu Guide: Hardy" link. I've printed the guide to hard copy and a PDF. Thank you very much for that! With what I've read already, I'm feeling much more confident that I'll be able to upgrade without getting in way over my head.

---


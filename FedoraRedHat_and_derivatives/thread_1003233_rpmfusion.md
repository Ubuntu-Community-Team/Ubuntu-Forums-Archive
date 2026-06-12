---
title: "rpmfusion"
date: 2008-12-05
forum: Fedora/RedHat and derivatives
---

### Post by mr.farenheit on 2008-12-05
i've been running mainly ubuntu lately but have for the longest time been a fan of RHDL. i heard or something called rpmfusion and the way people are talking of it they make it sound like something of the automatix sort but for fedora. if so whats involved with it(a/v codecs, java, adobe etc)?

---

### Post by djhyland on 2008-12-05
RPMFusion is a third-party repository that, among other things, contains license-encumbered packages.  So all your shady codecs, dvd support, binary drivers, and the like can be found there.

I've never used Automatix, but isn't that a third-party program that sets stuff up for you?  If so, RPMFusion isn't like that.  To use it, go to their web page.  They'll have instructions on adding the repo to your  software sources.  After doing that, you'll be able to access the contents of it through your normal package management method like PackageKit or yum from the command line or whatever else you might use.

Hope this helps!

---

### Post by igknighted on 2008-12-05
> **mr.farenheit said:**
> i've been running mainly ubuntu lately but have for the longest time been a fan of RHDL. i heard or something called rpmfusion and the way people are talking of it they make it sound like something of the automatix sort but for fedora. if so whats involved with it(a/v codecs, java, adobe etc)?

It's just like Medibuntu for Ubuntu, or PLF (Penguin Liberation Front) for Mandriva, or Pacman/Videolan for Suse.  Just houses packages that the distribution wont package (codecs, non-free drivers, etc.).  Basically RPMFusion combined Freshrpms, Atrpms, and Livna to avoid users installing from both and mucking up their systems.  So it does simplify install for the users, but doesn't automate anything.

---

### Post by mr.farenheit on 2008-12-05
awesome thx

---

### Post by igknighted on 2008-12-05
I've never tried this, but this seems like an automatix clone for fedora:

[http://easylifeproject.org/](http://easylifeproject.org/)

---

### Post by ibutho on 2008-12-05
RPMfusion is basically a third party Fedora repository that was formed when developers from several repos decided to work together instead of maintaining separate repositories. Previously there were several different repositories that were not always compatible with each other and mixing them could sometimes have undesirable results.

---


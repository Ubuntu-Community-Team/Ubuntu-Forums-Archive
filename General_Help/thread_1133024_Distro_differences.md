---
title: "Distro differences"
date: 2009-04-22
forum: General Help
---

### Post by Mistoffeles on 2009-04-22
Is there an article or thread anywhere that clearly reviews the differences between the Ubuntu/Debian and RedHat/Fedora branches of Linux? For example, where common things are kept, what the differences in install, boot, and control processes are, how to control the use of the GUI, etc. and things like how Ubuntu uses apt-get + dpkg to cover the complete functionality of yum (which really messed me up for a while)?

I find bits and pieces, but never a comprehensive (or close to comprehensive) document.

---

### Post by snowpine on 2009-04-22
Check out [www.distrowatch.com](www.distrowatch.com)
It is a really great database comparing the different distros.

---

### Post by Mistoffeles on 2009-04-22
Distrowatch doesn't even begin to go into the breadth or depth of detail I am looking for here, at most there is a blurb and a link to each distro's website.

---

### Post by mb_webguy on 2009-04-22
I don't know that you're going to find much more detail than that provided by the Distrowatch and Wikipedia entries on the distributions.

Debian is purely a community effort, and not maintained, supported, or sponsored by a company.  Red Hat Enterprise Linux is a commercial distribution, and Fedora (the free, community-maintained version) is sponsored by Red Hat.

Debian is built on the philosophy of being 100% FOSS.  Fedora is, as previously mentioned, an offshoot of a commercial product, and while it advocates FOSS, it isn't as devoted to the philosophy as Debian.

Debian is composed of three different but cooperative distributions: stable, testing, and unstable.  The stable version has a stepped release schedule, while the other two use rolling releases.  Fedora uses a stepped release schedule.

Debian uses deb software packages, while Fedora uses rpm packages.  Once upon a time, Red Hat-based distributions only had a fraction of the number of available software packages as Debian, and no comparable package management systems.  Since Red Hat split into RHEL and Fedora, however, this isn't really the case, and software management on Fedora and Debian is more or less equivalent.  Some people would argue that rpm packages are better than deb packages since they don't rely on Debian naming conventions and are therefore more distribution-agnostic, but there's no practical difference in terms of using either on a distribution for which they're designed to be used.

And, of course, Debian and Fedora use different default applications, though this is true of every distribution.

Really, in some ways, Ubuntu is more like Fedora than Debian, even though it is a Debian-based distribution, since it's backed by a company (Canonical) and has a stepped release schedule.  But since it's built on Debian packages uses the same package management system, it's a Debian-based distribution.

When you get down to the basics, Linux is Linux.  Everything else is just software running on top of it.  And it's only the differences in default software that determines the distribution.

---

### Post by aeiah on 2009-04-22
ive tried to find a similar thing a few times and always come up short. if you have the time, grab the live fedora disk image and have a play. fedora by default uses gnome and you'll find it to be very similar. if you've been using ubuntu much the differences will be fairly obvious.

we use fedora at work and i have to use the gui and cli from time to time and apart from a few things not being there that id expect its pretty much the same. i havent configured anything unusual under fedora though which is probably why i havent come across many differences.

---


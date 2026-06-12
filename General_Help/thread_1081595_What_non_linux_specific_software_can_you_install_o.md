---
title: "What non linux specific software can you install on linux platforms?"
date: 2009-02-26
forum: General Help
---

### Post by Macfunky on 2009-02-26
Just installed opera yesterday and it got me thinking. What useful software is out there that doesn't come in the repositories? Anyone have any particular favorites?

Also when i do find a software which extension am i looking for to use it with ubuntu? I still sometimes get confused with this. Thanks everyone.

---

### Post by howefield on 2009-02-26
.deb is the format which Ubuntu uses.

You can convert .rpm to .deb using a program called Alien.

And of course you can install from source, but it is normally recommended to use a repository in order to get program updates.

---

### Post by mb_webguy on 2009-02-26
> **Macfunky said:**
> Just installed opera yesterday and it got me thinking. What useful software is out there that doesn't come in the repositories? Anyone have any particular favorites?

Also when i do find a software which extension am i looking for to use it with ubuntu? I still sometimes get confused with this. Thanks everyone.

Your post doesn't match your title.  Linux runs Linux software.  Short of something like [Wine]("http://www.winehq.org/"), you can't run non-Linux software on Linux any more than you can run non-Windows or non-Mac software on those operating systems.

If you're talking about software *for Linux* that's not in the Ubuntu repositories, then... well, most of the popular Linux software *is* in the repositories.  For software that isn't, you need to look for deb files (as howefield said).  There are basically two main families of Linux distributions -- Debian and Red Hat.  Red Hat-based distributions use rpm files to distribute software, while Debian-based distributions (including Ubuntu) use deb files to distribute software.  While rpm files *can* be converted to deb files, they're really not compatible with each other, and you're likely to run into problems trying to install software from an rpm on Ubuntu.

You can usually find deb files on the web page for a software project.  Sites like [GetDeb]("http://www.getdeb.net/") provide debs for a variety of software.  However, software installed from deb files will not be automatically updated like software installed from the repositories.  For this reason, I prefer to use [Launchpad]("https://launchpad.net/") PPAs, which are like mini-repositories, whenever possible.

---

### Post by rhosigma on 2009-02-26
I would recommend the getdeb website: [http://www.getdeb.net]("http://www.getdeb.net"). This site has may applications and games. Some software is included in the repositories but updated, and some that are not in the repos. Ubuntu tweak is a personal favorite of mine. It has many great tweaks; one of which will add additional sources to your repo list of popular applications. That is if this thread is talking about native Linux software and not "non Linux specific software" per your title

---


---
title: "Using 8.04 LTS; can I update one package to 8.10 or later?"
date: 2009-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by romandas on 2009-05-19
Hi all,

I'm using Ubuntu Hardy (8.04 LTS) that shipped with my Dell Studio 1535 laptop. I keep it patched as patches come out, but one package I use (on another system) has a bug in it in the 8.04 release, mit-scheme. See bug 217792 for details.

The bug has been closed, but the updated mit-scheme package is only available from Intrepid-updates or later. Is there any way to have the Software Updater or the Synaptic Package Manager see updates for just mit-scheme so I can update and rid myself of the buggy current package and still have mit-scheme maintained by the package managers?

---

### Post by Brandon Williams on 2009-05-20
[This documentation](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html) explains how to do what you are looking to do, starting with section 3.8. I'm not sure how complex this is going to end up being for you, since I've never done this on Ubuntu, only back when I was still using Debian.

I haven't looked at this specific package, but it's important to note that there are some packages that will end up forcing you to pull the whole system in just to install that version of the software.

Just out of curiosity, before you go this route, have you double-checked to make sure that the version you want isn't in hardy-backports?

---


---
title: "Can Ubuntu executable run on Knoppix (and vice versa)"
date: 2006-03-13
forum: Desktop Environments
---

### Post by sbasak on 2006-03-13
Is it possible to run an Ubuntu executable file in Knoppix and vice versa?

I copied Nautilus from Ubuntu to Knoppix. In Knoppix, it is running, but the interface looks a bit awkward (compared to Nautilus in Ubuntu). Also, during runtime, it shows some error message in console.

A "Hello World" program programmed by cc in Knoppix simply doesn't run in Ubuntu.

Since both Knoppix & Ubuntu are based on Debian, why there is difference?

Thanx for replies.

---

### Post by meborc on 2006-03-13
hmm... did you **sudo apt-get install hello**? ... i see that "Hello World" is in repositories (universe)... i guess there are some dependencies that need to be met... i can't see why don't you use apt-get as it is the easyest way of installing things... :mrgreen: 

see [https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto) for apt-get
and [http://packages.ubuntulinux.org/breezy/devel/hello](http://packages.ubuntulinux.org/breezy/devel/hello) for packages (but use the command above for installing)

---


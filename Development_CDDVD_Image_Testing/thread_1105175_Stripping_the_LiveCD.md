---
title: "Stripping the LiveCD"
date: 2009-03-24
forum: Development CD/DVD Image Testing
---

### Post by Jonnox on 2009-03-24
Hi,

Quick question. I am modifying the Live CD for Ubuntu (adding / removing packages) to create a unique environment. The problem is, when I make the CD, it still boots initially asking "Do you want to install, try Ubuntu without installing...". Is there a way to remove this? I need an image that JUST loads right into the Ubuntu live CD without allowing people to install it. Any ideas?

Thanks in advance.

P.S. If this is in the wrong forums, could someone move it to the more appropriate section. Thank you.

---

### Post by mocoloco on 2009-03-24
First of all, you want to use an app called [reconstructor]("http://reconstructor.aperantis.com/").  I've done something similar to what you're saying.  One of reconstructor's options is to open a root console for your new liveCD, and from there you want to uninstall the graphical installer app, called ubiquity.  You can also edit the beginning menu (the one before anything boots) and remove some of the options. There are some files you can edit for that, I don't remember where they are, not on the machine where I set that up but I can post back later.

---

### Post by Jonnox on 2009-03-25
Thanks for such a prompt reply! I will check that out. If you think of anything else I'll check the post again. :) Thanks again!

---

### Post by Crispian Troy on 2009-08-12
This hint should guide you through the process of building a LFS
system using the LFS live CD as the host operating system.  You use
the LFS live CD to boot the computer instead of loading a pre-
packaged linux distribution like Debian or Red Hat.  This is the
"cleanest" way to build a LFS system, since inconsistancies and
idiosyncracies of the various distributions are removed.

---

### Post by nikhilbhardwaj on 2009-09-10
> **Crispian Troy said:**
> You use
the LFS live CD to boot the computer instead of loading a pre-
packaged linux distribution like Debian or Red Hat.  This is the
"cleanest" way to build a LFS system, since inconsistancies and
idiosyncracies of the various distributions are removed.

i dont understand what you mean by the "cleanest"
the lfs system builds itself
the host is only needed to make a temporary toolchain which is later discarded
so one can use any linux distro to complete the build
continuing from where you left off with the live cd is a real pain

---


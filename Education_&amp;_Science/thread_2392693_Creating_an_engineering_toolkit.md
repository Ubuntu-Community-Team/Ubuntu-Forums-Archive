---
title: "Creating an engineering toolkit"
date: 2018-05-24
forum: Education &amp; Science
---

### Post by jordana309 on 2018-05-24
I am looking to create an engineering system that I can leave with my university that will have a host of languages and useful tools on it so that engineers can spend more time getting to work and less time trying to figure out how to set things up. I have since decided that the work I'm putting into that would likely benefit other engineers, so I have created the skeleton for the project on GitHub ([https://github.com/jordana309/EngineeringInLinux/tree/master](https://github.com/jordana309/EngineeringInLinux/tree/master)). That project includes a list of the tools I'm trying to incorporate, and the How to Run this System.odt file is my working install record documenting what I've done so far.

I'm asking for general thoughts from those who've used Ubuntu for engineering applications, and from others for ideas on IDEs and other tools to include. I'm aiming to have the full system be about 100 GB, but be capable of just about common thing an engineer might encounter. Would anybody be interested in helping me figure out what to put in or take out?

I currently have my virtual box set up through all the languages, and all the kernels in Jupyter work. Everything after that is new territory for me, though...

---

### Post by TheFu on 2018-05-24
How will they maintain all these installed tools?  A system that can't be maintained is out of date in just a few months. Getting all the tools into a debian repo with a package maintainer would be very helpful.

ASE here, BTW.

---

### Post by jordana309 on 2018-05-24
I'm trying to get as much as I can from repos, but some things require very new versions to run, so I need to get them elsewhere. For those tools, I will include instructions for updating (many of the tools have their own updaters), and I try to get pre-compiled binaries so that updating is as easy as downloading the new version. That's a good suggestion, though--maybe you can help me see where I could use a repo but didn't?

---


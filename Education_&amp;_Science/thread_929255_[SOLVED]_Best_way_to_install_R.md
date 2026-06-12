---
title: "[SOLVED] Best way to install R?"
date: 2008-09-24
forum: Education &amp; Science
---

### Post by OldDirtyTurtle on 2008-09-24
OK...  As a total newbie, I'm wondering what's the easiest way to install the latest version of R?  

I'm completely confused.  I've started the directions in the community help docs on compiling from a tarball, but it feels kind of treacherous for a new-to-linux person like me.

:confused:

---

### Post by hubie on 2008-09-24
Do you need the absolute latest and greatest R?  If not, you can just install r-base from the package manager.

If you really want the latest and greatest, some nice step-by-step instructions are [here]("http://edtechdev.blogspot.com/2007/08/getting-r-set-up-in-ubuntu.html").

---

### Post by DrOlaf on 2008-09-24
I just added my local CRAN mirror to my sources.list, and used apt-get, aptitude, or synaptic to pull it over. The versions there are recent enough for me.

This link should help you out:

[http://cran.r-project.org/doc/FAQ/R-FAQ.html#Are-there-Unix-binaries-for-R_003f]("http://cran.r-project.org/doc/FAQ/R-FAQ.html#Are-there-Unix-binaries-for-R_003f")

---

### Post by OldDirtyTurtle on 2008-09-24
Got it...  Dug a little bit deeper on [http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/) and followed the directions.  Turned out to be less of a problem than I thought.

---

### Post by earlycj5 on 2008-09-25
> **OldDirtyTurtle said:**
> Got it...  Dug a little bit deeper on [http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/) and followed the directions.  Turned out to be less of a problem than I thought.

Did you get the gpg key to work?

Mine is still unverified.

---

### Post by OldDirtyTurtle on 2008-09-25
I think I did it a bit out of order.  I installed the packages anyway when I got the warning that the download was unverified.  I later noticed the key recommendations and used the terminal to install the key.  It shows up, but I've no idea if it is verified or not.

That'll teach me to not read the entire set of directions before proceeding...  :wink:

How do I check to see if the key is verified?

> **earlycj5 said:**
> Did you get the gpg key to work?

Mine is still unverified.

---


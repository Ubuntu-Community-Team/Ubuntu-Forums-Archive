---
title: "MCMC++ installation issues (Bayesian Statistics)"
date: 2008-01-05
forum: Education &amp; Science
---

### Post by drexell0680 on 2008-01-05
Has anyone got this to work with Ubuntu?   R can't seem to find the package on any server I try...

Thanks,
DGP

---

### Post by euler_fan on 2008-01-08
Three questions:

1) Did you start R as sudo? If you don't even if it gets it R won't install it.
2) Is it really in CRAN? I assume yes . . . 
3) Have you tried downloading it to your desktop, running R as sudo, and installing it from the local *.tar.gz file?

EF

---

### Post by euler_fan on 2008-01-08
Okay, [this package from the University of Minnesota]("http://cran.r-project.org/src/contrib/Descriptions/mcmc.html") is in CRAN. I don't see an MCMC++ package though.

There's also [this one]("http://cran.r-project.org/src/contrib/Descriptions/MCMCpack.html").

At this point I'd say just download it and install it locally. It's slightly less fun but no more difficult.

---

### Post by drexell0680 on 2008-01-10
Thanks for the response, let me apologize beforehand for the confusion.  Initially I'd posted in relation to MCMC++ (are you running this btw?) but have since realized it's simply a c++ library of which I was missing other (unspecified) libraries to compile.

My next question was intended to be about Rcommander, a package for R providing a GUI as I found it unsettling to not have pull down menus as in the windows version.  Installing locally works though, thank you.

Let me know about mcmc++ though, I still can't get the libraries to automatically install to my includes and libraries.

DGP

---

### Post by euler_fan on 2008-01-10
> **drexell0680 said:**
> Thanks for the response, let me apologize beforehand for the confusion.  Initially I'd posted in relation to MCMC++ (are you running this btw?) but have since realized it's simply a c++ library of which I was missing other (unspecified) libraries to compile.

My next question was intended to be about Rcommander, a package for R providing a GUI as I found it unsettling to not have pull down menus as in the windows version.  Installing locally works though, thank you.

Let me know about mcmc++ though, I still can't get the libraries to automatically install to my includes and libraries.

DGP

About MCMC++:

That explains why I couldn't find it on CRAN. I'm not running it personally.

About Rcommander:

I don't use a GUI with R except for the one I use for VIM to write script files for it. If you don't like that particular one there are any number of others out there. If you look back in this forum for a bit you'll find a thread for a popular java-based gui for R which I think is called JGR. You could also try getting the most recent version from the authors/maintainers directly and installing it locally.

---


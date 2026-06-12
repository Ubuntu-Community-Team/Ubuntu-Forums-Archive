---
title: "Installing wine errors"
date: 2009-03-17
forum: General Help
---

### Post by a2z on 2009-03-17
I have been trying to install wine without success for ever. I'm new to Ubuntu so I don't know much about error messages. Or how to rectify them. I did however come across this site [http://www.ubuntu-unleashed.com/2008/05/howto-install-latest-wine-in-ubuntu.html]("http://www.ubuntu-unleashed.com/2008/05/howto-install-latest-wine-in-ubuntu.html") which provided me with the most advances installing this software. In conclusion, I believe there is an installation bug as stated here:
[B]
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
E: Broken packages[/B]

I have also noticed the Wine site is currently down. I hope they already recognize the problem and are  in the process of fixing it. 

I'm using Ubuntu 8.10

---

### Post by LegendofTom on 2009-03-17
ia32-libs is a problem with 64 bit architechture.  Are you running 64 bit Ubuntu by chance?

---

